import UIKit
import CoreLocation

class ViewController: UIViewController {

    let locationManager = CLLocationManager()
        
    override func viewDidLoad() {
        super.viewDidLoad()
        
        locationManager.requestAlwaysAuthorization()
        
        }
        
        }
