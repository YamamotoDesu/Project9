# Project9
<img width="300" alt="スクリーンショット 2023-03-11 15 01 52" src="https://user-images.githubusercontent.com/47273077/224467972-3c12a1ff-d8c6-47f6-adbe-a84e47752504.png">

```swift
struct Triangle: Shape {
    func path(in rect: CGRect) -> Path {
        var path = Path()
        
        path.move(to: CGPoint(x: rect.midX, y: rect.minY))
        path.addLine(to: CGPoint(x: rect.minX, y: rect.maxY))
        path.addLine(to: CGPoint(x: rect.maxX, y: rect.maxY))
        path.addLine(to: CGPoint(x: rect.midX, y: rect.minY))
        
        return path
    }
}

 Triangle()
            .stroke(.red, style: StrokeStyle(lineWidth: 10, lineCap: .round, lineJoin: .round))
            .frame(width: 300, height: 300
```

<img width="300" alt="スクリーンショット 2023-03-11 15 01 52" src="https://user-images.githubusercontent.com/47273077/224467972-3c12a1ff-d8c6-47f6-adbe-a84e47752504.png">

```swift
struct Arc: Shape {
    let startAngle: Angle
    let endAngle: Angle
    let clockwise: Bool
    
    func path(in rect: CGRect) -> Path {
        var path = Path()
        
        path.addArc(center: CGPoint(x: rect.minX, y: rect.minY), radius: rect.width / 2, startAngle: startAngle, endAngle: startAngle, clockwise: clockwise)
        
        return path
    }
}
```

<img width="300" alt="スクリーンショット 2023-03-11 15 20 48" src="https://user-images.githubusercontent.com/47273077/224468691-11e5018c-36fb-4b2a-a963-7a0cafb3f7b8.png">

```swift
struct Arc: Shape {
    let startAngle: Angle
    let endAngle: Angle
    let clockwise: Bool
    
    func path(in rect: CGRect) -> Path {
        let rotationAdjustment = Angle.degrees(90)
        let modifiedStart = startAngle - rotationAdjustment
        let modifiedEnd = endAngle - rotationAdjustment

        var path = Path()
        
        path.addArc(center: CGPoint(x: rect.midX, y: rect.midY), radius: rect.width / 2, startAngle: modifiedStart, endAngle: modifiedEnd, clockwise: clockwise)
        
        return path
    }
}

        Arc(startAngle: .degrees(0), endAngle: .degrees(40), clockwise: true)
            .stroke(.blue, lineWidth: 10)
            .frame(width: 300, height: 300)
```


