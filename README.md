# 🧮 SwiftUI Calculator App

![Swift](https://img.shields.io/badge/Swift-5.9-orange?logo=swift)
![SwiftUI](https://img.shields.io/badge/SwiftUI-Framework-blue?logo=swift)
![Xcode](https://img.shields.io/badge/Xcode-15-blue?logo=xcode)
![iOS](https://img.shields.io/badge/iOS-17-lightgrey?logo=apple)

A simple **Calculator app** built using **SwiftUI**.  
Supports basic arithmetic operations (**addition, subtraction, multiplication, division**) with a custom numeric keypad.

---

## 📸 Preview
The UI includes:
- A **display field** showing the current result and input.
- A **numeric keypad (0–9)**.
- Operation buttons: `+`, `-`, `X`, `/`, and `=`.
- A **dark mode friendly** layout with styled buttons.

---

## 📂 Project Structure
```
Calculator/
├── ContentView.swift # Main calculator UI & logic
├── CalculatorApp.swift # App entry point
```

---

## 🚀 Features
- ✅ Input numbers using custom buttons.  
- ✅ Perform **addition, subtraction, multiplication, division**.  
- ✅ Display intermediate results.  
- ✅ Equals (`=`) executes the last selected operation.  
- ✅ Clear and simple SwiftUI layout.  

---

## ▶️ Running the App
1. Open project in **Xcode**.
2. Run on **iPhone Simulator** or real device.
3. Start performing calculations 🎉.

---

## 🛠️ Future Improvements
- Add a **Clear (C)** button.  
- Support **decimal input** (`.` button not yet implemented).  
- Improve error handling (e.g., divide by zero).  
- Add **history log** for past calculations.  

---

## 📄 Full Code

```swift
//
//  ContentView.swift
//  Calculator
//
//  Created by Matthew Lim on 14/8/25.
//

import SwiftUI

struct ContentView: View {
    
    // Model
    @State private var userInput: String = ""
    @State private var totalNumbers: Float = 0
    @State private var displayTotalNumbers: String = ""
    @State private var LastClickedButton: String? = nil
    
    var body: some View {
        
        ZStack {
            
            Color.black.edgesIgnoringSafeArea(.all)
            
            //View
            VStack {
                
                HStack {
                    
                    TextField("Result", text: $displayTotalNumbers)
                        .multilineTextAlignment(.trailing)
                        .font(.system(size:30))
                        .foregroundColor(.white)
                        .keyboardType(.numberPad)
                        .padding()
                    
                }
                
                HStack {
                    
                    TextField("Enter a number", text: $userInput)
                        .multilineTextAlignment(.trailing)
                        .font(.system(size:40))
                        .foregroundColor(.white)
                        .keyboardType(.numberPad)
                        .padding()
                    
                }
                
                HStack {
                    
                    Button("7"){
                        userInput.append("\(7)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("8"){
                        userInput.append("\(8)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("9"){
                        userInput.append("\(9)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("X"){
                        multiplyButton()
                        LastClickedButton = "X"
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.orange.opacity(0.8))
                        .cornerRadius(10)
                }
                
                HStack {
                    
                    Button("4"){
                        userInput.append("\(4)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("5"){
                        userInput.append("\(5)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("6"){
                        userInput.append("\(6)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("-"){
                        substractButton()
                        LastClickedButton = "-"
                        userInput = ""
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.orange.opacity(0.8))
                        .cornerRadius(10)
                }
                
                HStack {
                    
                    Button("1"){
                        userInput.append("\(1)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("2"){
                        userInput.append("\(2)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("3"){
                        userInput.append("\(3)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("+"){
                        addButton()
                        LastClickedButton = "+"
                        userInput = ""
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.orange.opacity(0.8))
                        .cornerRadius(10)
                }
                HStack {
                    
                    Button("0"){
                        userInput.append("\(0)")
                        
                    }
                    .font(.largeTitle)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity, alignment: .center)
                    .background(Color.gray.opacity(0.8))
                    .cornerRadius(10)
                    
                    Button("."){
                        
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.gray.opacity(0.8))
                        .cornerRadius(10)
                    
                    Button("="){
                        equalButton()
                        LastClickedButton = "="
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.gray.opacity(0.8))
                        .cornerRadius(10)
                    
                    Button("/"){
                        divideButton()
                        LastClickedButton = "/"
                        userInput = ""
                    }.font(.largeTitle)
                        .foregroundColor(.white)
                        .padding()
                        .frame(maxWidth: .infinity, alignment: .center)
                        .background(Color.orange.opacity(0.8))
                        .cornerRadius(10)
                }
            }
            
        }
        
       
    }
    
    // View Model
    func addButton() {
        if let number = Float(userInput) {
            totalNumbers += Float(number)
            displayTotalNumbers = "\(totalNumbers) + "
            userInput = ""
        }
    }
    
    func substractButton() {
        if let number = Float(userInput) {
            if totalNumbers == 0 {
                totalNumbers = 2 * Float(number)
            }
            totalNumbers -= Float(number)
            displayTotalNumbers = "\(totalNumbers) - "
            userInput = ""
        }
    }
    
    func multiplyButton() {
        if let number = Float(userInput) {
            if totalNumbers == 0 {
                totalNumbers = 1
            }
            totalNumbers *= Float(number)
            displayTotalNumbers = "\(totalNumbers) X "
            userInput = ""
        }
    }
    
    func divideButton() {
        if let number = Float(userInput) {
            if totalNumbers == 0 {
                totalNumbers = Float(number)
                totalNumbers *= totalNumbers
            }
            totalNumbers /= Float(number)
            displayTotalNumbers = "\(totalNumbers) / "
            userInput = ""
        }
    }
    
    func equalButton() {
        checkLastClickButton()
        displayTotalNumbers = "\(totalNumbers)"
        userInput = ""
    }
    
    func checkLastClickButton() {
        if LastClickedButton == "+" {
            totalNumbers += Float(userInput) ?? 0
        }
        else if LastClickedButton == "-" {
            totalNumbers -= Float(userInput) ?? 0
        }
        else if LastClickedButton == "X" {
            totalNumbers *= Float(userInput) ?? 0
        }
        else if LastClickedButton == "/" {
            totalNumbers /= Float(userInput) ?? 0
        }
        
    }
}

#Preview {
    ContentView()
}
