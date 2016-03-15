
Based on variable names, Liquid returns values on six different data types: `NSString`, `UIColor`, `NSDate`, `NSInteger`, `CGFloat` and `BOOL`. These methods return the `fallbackValue` if the value is not present or valid.

{% highlight swift %}
- (NSString *)stringForKey:(NSString *)variableName fallback:(NSString *)fallbackValue;
- (UIColor *)colorForKey:(NSString *)variableName fallback:(UIColor *)fallbackValue;
- (NSDate *)dateForKey:(NSString *)variableName fallback:(NSDate *)fallbackValue;
- (NSInteger)intForKey:(NSString *)variableName fallback:(NSInteger)fallbackValue;
- (CGFloat)floatForKey:(NSString *)variableName fallback:(CGFloat)fallbackValue;
- (BOOL)boolForKey:(NSString *)variableName fallback:(BOOL)fallbackValue;
{% endhighlight %}
