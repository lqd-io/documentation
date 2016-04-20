
Most of the times, it is useful to have all dynamic variables and their fallback values in the same place.

This kind of practice not only improves code organization and readability, but also reutilization of static values in your code.

This way, we recommend you to create `FallbackVariables.{h,m}` files, like shown on the example below:

{% highlight swift %}
// FallbackVariables.h

#import &lt;Foundation/Foundation.h&gt;

@interface FallbackValues : NSObject

extern NSString *const defaultTitle;
extern NSString *const defaultBgColor;
extern NSString *const defaultPromoDay;
extern NSInteger const defaultloginVersion;
extern CGFloat const defaultDiscount;
extern BOOL const defaultShowAds;

@end
{% endhighlight %}

{% highlight swift %}
// FallbackVariables.m

#import "FallbackValues.h"

@implementation FallbackValues

NSString *const defaultTitle = @"Welcome to our app";
NSString *const defaultBgColor = @"#FF00FF";
NSString *const defaultPromoDay = @"2014-05-11T15:17:03.103+0100";
NSInteger const defaultloginVersion = 3;
CGFloat const defaultDiscount = 0.15f;
BOOL const defaultShowAds = YES;

@end
{% endhighlight %}

By doing this, you can now use dynamic Liquid variables like:

{% highlight swift %}
NSString *title = [[Liquid sharedInstance] stringForKey:@"title" fallback:defaultTitle];
NSDate *promoDay = [[Liquid sharedInstance] dateForKey:@"promoDay" fallback:[Liquid gettDateFromISO8601String:defaultPromoDay]];
UIColor *bgcolor = [[Liquid sharedInstance] colorForKey:@"textcolor" fallback:[Liquid colorFromString:defaultBgColor]];
NSInteger loginVersion = [[Liquid sharedInstance] intForKey:@"login" fallback:defaultloginVersion];
CGFloat discount = [[Liquid sharedInstance] floatForKey:@"discount" fallback:defaultDiscount];
BOOL showAds = [[Liquid sharedInstance] boolForKey:@"showAds" fallback:defaultShowAds];
{% endhighlight %}

while keeping a list of your dynamic variables and fallback values in one unique place.

{% include alert.md type='warning' message="Most of the times, you'll want to make sure that your **default values** (in Liquid dashboard) are the same as the **fallback values** (in your code)." %}
