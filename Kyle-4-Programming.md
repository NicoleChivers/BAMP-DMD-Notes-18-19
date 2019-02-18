# Programming


//for requesting permission to use location
//include in info.plist (bottom of first file list)
//Privacy - Location Always and When In Use Usage Description 
//Privacy - Location When In Use Usage Description

import UIKit
import CoreLocation
import MapKit

class ViewController: UIViewController {
    let locationManager = CLLocationManager()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        locationManager.requestAlwaysAuthorization()
        locationManager.delegate = self
        locationManager.startUpdatingLocation()
        
        let coordinate = CLLocationCoordinate2D(latitude: 50.753019, longitude: -1.930140)
        let region = CLCircularRegion(center: coordinate, radius: 300, identifier: "Region")
        locationManager.startMonitoring(for: region)
    
        let newCoordinate = CLLocationCoordinate2D(latitude: 50.742553, longitude: -1.892333)
        let newRegion = CLCircularRegion(center: newCoordinate, radius: 300, identifier: "New")
        locationManager.startMonitoring(for: newRegion)

        let extraCoordinate = CLLocationCoordinate2D(latitude: 50.761153, longitude: -1.874836)
        let extraRegion = CLCircularRegion(center: extraCoordinate, radius: 300, identifier: "Extra")
        locationManager.startMonitoring(for: extraRegion)
    }
}

extension ViewController: CLLocationManagerDelegate{
    func locationManager(_ mananger: CLLocationManager, didUpdateLocations locations: [CLLocation]){
//        print(locations.last!)
    }
    func locationManager(_ manager: CLLocationManager, didEnterRegion region: CLRegion) {
        print("Enter: \(region.identifier)")
    }
    func locationManager(_ manager: CLLocationManager, didExitRegion region: CLRegion) {
        print("Exit: \(region.identifier)")
    }
}
