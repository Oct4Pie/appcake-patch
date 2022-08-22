# Appcake 7.2.2 Patch
The crash and certificate issues are fixed.
The signing still does not work since appcake's certificates are revoked.
If you know how to go about fixing this, please open an issue.
# Main cause of crashes
```armasm
r0 = [r21 objectForKeyedSubscript:@"output"];
r0 = [r0 retain];
var_60 = r0;
r0 = [r0 objectAtIndex:0x0];
r0 = [r0 retain];
```
The call to `objectAtIndex` raised NSArray Out of Bounds Exception.
This is because no valid certificates are present.