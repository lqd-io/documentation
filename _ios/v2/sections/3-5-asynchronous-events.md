
Optionally you can be notified of Liquid internal internal events by implementing `LiquidDelegate` or `NSNotificationCenter` interface on your code, to take action when:

* When values are received from Liquid dashboard (not necessarily loaded)
* When values are loaded

Liquid triggers two types of notifications: `LQDidReceiveValues` and `LQDidLoadValues` corresponding both situations above.

Follow the steps for your prefered method to receive these notifications in your code.

#### via NSNotificationCenter

{% highlight swift %}
// ViewController.m

- (void)viewDidLoad {
  NSNotificationCenter *notificationCenter = [NSNotificationCenter defaultCenter];
  [notificationCenter addObserver:self name:LQDidReceiveValues
                         selector:@selector(newValues:) object:nil];
  [notificationCenter addObserver:self name:LQDidLoadValues
                         selector:@selector(loadValues:) object:nil];
  // The rest of your code goes here...
}

- (void)newValues:(NSNotification *)notification {
  // Do somthing, e.g: [[Liquid sharedInstance] loadNewValues];
}

- (void)loadValues:(NSNotification *)notification {
  // Do something with new variables, e.g: refresh a view
}
{% endhighlight %}

#### via LiquidDelegate

Because Liquid shared instance is a singleton, you can only set one of your objects as delegated to Liquid events.

As an example, let's assume you want to delegate this events to one of your View Controllers. Your header file would be something like:

{% highlight swift %}
// ViewController.h

#import "Liquid.h"

@interface ViewController : UIViewController &lt;LiquidDelegate&gt;
{% endhighlight %}

and your implementation file would be like:

{% highlight swift %}
// ViewController.m

- (void)viewDidLoad {
  [super viewDidLoad];
  [[Liquid sharedInstance] setDelegate:self];
  // The rest of your code goes here...
}

- (void)liquidDidReceiveValues {
  // Do somthing with new values, e.g: [[Liquid sharedInstance] loadNewValues];
}

- (void)liquidDidLoadValues {
  // Do something with new variables, e.g: refresh a view
}
{% endhighlight %}
