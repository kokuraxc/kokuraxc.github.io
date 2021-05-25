> Inject a Transient service into the BackgroundService

In my current .Net Core microservice project (Asset Manager microservice), I needed to implement a background service to check and increase the asset features' values.

```cs
using System;
using System.Threading;
using System.Threading.Tasks;
using AssetManager.Domain.Models.AssetAggregate;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

namespace AssetManager.API.BackgroundServices
{
    public class AssetFeatureAutoIncrementService : BackgroundService
    {
        public IAssetRepository _assetRepository;

        public AssetFeatureAutoIncrementService(IAssetRepository assetRepository)
        {
            _assetRepository = assetRepository;
        }

        protected async override Task ExecuteAsync(CancellationToken stoppingToken)
        {
            while (!stoppingToken.IsCancellationRequested)
            {
                await Task.Delay(TimeSpan.FromMinutes(30)); // check every 30 mins
                await _assetRepository.AutoIncreaseAssetsFeatureAsync(1);
            }
        }
    }
}
```
This ran into some runtime error, reason being that the BackgroundSerice is singleton while the IAssetRepository is transient, as showned by the following code.

```cs
services.AddTransient<IAssetRepository, AssetRepository>();
```

Reading from this [stack**overflow**](https://stackoverflow.com/a/38139500) I understood that it's ok to put a singleton in a transient, but the other way around won't work, which my previous codes demoed.

The modified codes go as follows:

```cs
namespace AssetManager.API.BackgroundServices
{
    public class AssetFeatureAutoIncrementService : BackgroundService
    {
        public IServiceProvider Services;

        public AssetFeatureAutoIncrementService(IServiceProvider services)
        {
            Services = services;
        }

        protected async override Task ExecuteAsync(CancellationToken stoppingToken)
        {
            while (!stoppingToken.IsCancellationRequested)
            {
                await Task.Delay(TimeSpan.FromMinutes(30)); // check every 30 mins
                using (IServiceScope scope = Services.CreateScope())
                {
                    IAssetRepository assetRepository = scope.ServiceProvider.GetRequiredService<IAssetRepository>();
                    await assetRepository.AutoIncreaseAssetsFeatureAsync(1);
                }
            }
        }
    }
}
```

The BackgroundService was then added to services in the **ConfigureServices()** function in **Startup.cs**.
```cs
services.AddHostedService<AssetFeatureAutoIncrementService>();
```