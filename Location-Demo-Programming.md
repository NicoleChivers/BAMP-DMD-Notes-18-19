//  ViewController.swift
//  Location-Demo
//
//  Created by Nicole Chivers (s5113508) on 04/02/2019.
//  Copyright © 2019 Nicole Chivers (s5113508). All rights reserved.

import UIKit
import CoreLocation

class ViewController: UIViewController {

    let locationManager = CLLocationManager()
    @IBOutlet weak var locationLabel: UILabel!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        locationManager.requestAlwaysAuthorization()
        locationManager.delegate = self
        locationManager.startUpdatingLocation()
        
    }

}

extension ViewController: CLLocationManagerDelegate {
    
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        
    let location = locations.last!
        print(location.coordinate)
        locationLabel.text = "\(location.coordinate.latitude) \(location.coordinate.longitude)"
    }
}
