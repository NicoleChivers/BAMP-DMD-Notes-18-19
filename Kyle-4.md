# Workshop
for requesting permission to use location

include in info.plist (bottom of first file list)

Privacy - Location Always and When In Use Usage Description
Privacy - Location When In Use Usage Description

programming to cooperate with info.plist

import UIKit
import CoreLocation (not needed if you have imported MapKit)
import MapKit (if you have a map)

class ViewController: UIViewController {
       let locationManager = CLLocationManager()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        locationManager.requestAlwaysAuthorization()
        locationManager.delegate = self
        locationManager.startUpdatingLocation()
        }
}

extension ViewController: CLLocationManagerDelegate{
        func locationManager(_ mananger: CLLocationManager, didUpdateLocations locations: [CLLocation]){
        print(locations.last!)
        }
}
