BezierString
============

Rendering NSAttributedStrings along arbitrary continuous UIBezierPaths

## Example

![alt joe](https://raw.githubusercontent.com/lvnyk/BezierString/master/where.png)

### Create a bezier path and an attributed string

	let bezierPath = UIBezierPath()
	bezierPath.moveToPoint(CGPointMake(50, 50+150))
	bezierPath.addCurveToPoint(CGPointMake(50+200, 50), controlPoint1: CGPointMake(50+10, 50+75), controlPoint2: CGPointMake(50+100, 50))
	bezierPath.addCurveToPoint(CGPointMake(50+400, 50+150), controlPoint1: CGPointMake(50+300, 50), controlPoint2: CGPointMake(50+400-10, 50+75))
	
	let attributedString = NSAttributedString(string: "Where did you come from, where did you go?", attributes: [
		kCTFontAttributeName: CTFontCreateWithName("HelveticaNeue-UltraLight", 26, nil),
		kCTForegroundColorAttributeName: UIColor.redColor().CGColor
		])
	

### Use the BezierText class
	
	let bezierText = BezierText(bezierPath: bezierPath)
	
	// generate an image
	let img:UIImage! = bezierText.imageWithAttributedString(attributedString)	

	// or render onto a preexisting context
	bezierText.drawAttributedString(attributedString, toContext: UIGraphicsGetCurrentContext())