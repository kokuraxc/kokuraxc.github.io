### Three main components of EfficientDet:

1. Backbone: *EfficientNet*
2. Feature network to combine all features: *BiFPN*
3. Detection head

FPN gives equal importances to features of all the scales from P3 to P7. In EfficientDet, not all features contribute equally to the output features. Hence, a better strategy for multi-scale fusion is required.

#### Compound scaling
Scale the width, depth and resolution in a balanced way.

