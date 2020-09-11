** **

# Remita Inline Payment SDK for iOS


## Table of Contents

**OVERVIEW**

**1.0  IOS FRAMEWORK SETUP**

**2.0  TRY IT NOW**


## OVERVIEW

The following pages outlines the steps to integrating Remita Inline Payment SDK to your app.

## 1.0         Note: This setup is done on XCode 10.3, Swift 5.0.1, on Mac OS X(64bit) Mojave

**Step 1:** Go to **Add Files to < Project name > . . . ** 

**Step 2:** Click on **Copy tructure**

![](images/project_structure.JPG)
 

**Step 3:** Select **RemitaPaymentGateway.framework** drag and drop  under "Embedded Binaries" section to add the sdk  to your project.

 ![](images/modules.JPG)


**Step 5:** Rebuild project

** **



# 2.0         TRY IT NOW

You should invoke the RemitaInlinePaymentSDK.getInstance() at any point when making payment:


**Sample Code:**
```swift
import UIKit
import RemitaPaymentGateway

class ViewController: UIViewController, RemitaPaymentGatewayDelegate {

override func viewDidLoad() {
super.viewDidLoad()
// Do any additional setup after loading the view, typically from a nib.
}

override func didReceiveMemoryWarning() {
super.didReceiveMemoryWarning()
// Dispose of any resources that can be recreated.
}

@IBAction func payButton(_ sender: UIButton) {
let paymentGateway: RemitaPaymentGateway = RemitaPaymentGateway()
paymentGateway.delegate = self

let url: String = Constants.DEMO.rawValue

let txnId: String = UUID().uuidString.replacingOccurrences(of: "-", with: "")

paymentGateway.initiatePayment(on: self, url:url, key: "QzAwMDAxOTUwNjl8NDMyNTkxNjl8ZTg0MjI2MDg4MjU0NzA2NTY2MTYwNGU1NjNiMjUzYjk4ZDQwZjljZGFiMTVmYTljMDUwMGQ0MDg2MjIyYjEyNTA1ZTE2MTMxNmE3ZjM1OTZmYmJkOTE2MTRiY2NmZTY5NTM4MGQ2MDBlZGJlZmM2ODc2YTc2M2M4MjgyZmFjODc=", email: "lisa@spark.com", amount: "100", phoneNumber:"08037412366", firstname: "lisa", lastname: "Spark", customerId: "140700251", currencyCode: "NGN", transactionId: txnId, narration: "leather gucci bag")
}

func onPaymentCompleted(paymentResponse: PaymentResponse) {
print("+++ RESPONSE: \(String(describing: paymentResponse))")
}

}
 ```


Where url can be:

**Constants.DEMO.rawValue** (for testing) and **Constants.PRODUCTION.rawValue** (for live).

![](images/inline_snapshot.JPG)
