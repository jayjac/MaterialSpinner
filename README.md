# MaterialSpinner
Loading spinner based on Android's material design spinner

I tried to reproduce the spinning icon seen on Google's products.
All the necessary code is included in the *MaterialSpinner.swift* class.
Just copy that file into your own project.
Then, create a spinner either programmatically or from storyboard.

### Programmatically:
```swift
let spinner = MaterialSpinner(frame: CGRect(...), strokeColor: UIColor.green) // One stroke color
view.addSubview(spinner)
```

or for multiple stroke colors, use the following initializer.
The spinner will cycle through each color after every "stretch/retract" sequence

```swift
let spinner = MaterialSpinner(frame: CGRect(...), strokeColors: [UIColor.green, UIColor.blue]) //plural strokeColor*s*
view.addSubview(spinner)
```

You can tweak the lineWidth:
```swift
let spinner = MaterialSpinner(frame: CGRect(...), strokeColor: UIColor.green, lineWidth: 4.0 /* defaults to 2.0 */)
```

*isInteractive* option is if you want the initial stretching to be custom-made. For example, the user does a pan motion, and you want 
the spinner to strech or retract according to the pan gesture :

```swift
spinner.setInteractiveExtension(percent: /*float between 0.0 and 1.0*/ )
```
and then you call
```swift
spinner.startAnimationAfterInteractiveGesture()
```
when the spinner should resume spinning normally.


### Storyboard:
Drag a regular UIView on your UI, then set its class to MaterialSpinner.
Select the options from the attributes inspector (color, lineWidth, isInteractive)
Only one color can be set from the attributes inspector. If you want the spinner to be multicolored, connect it to an
outlet and use setStrokeColors(...)
```swift
@IBOutlet weak var spinner: MaterialSpinner!

...


    override func viewDidLoad() {
        super.viewDidLoad()
        spinner.setStrokeColors([UIColor.green, UIColor.yellow, UIColor.blue])
    }
```
```swift
