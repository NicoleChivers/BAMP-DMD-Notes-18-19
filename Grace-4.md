# View Controller

import UIKit
import MapKit

class ViewController: UIViewController {
    
    override func viewDidLoad() {
        super.viewDidLoad()
    }

    @IBOutlet weak var mapView: MKMapView!
        
    let someCoordinate = CLLocationCoordinate2D(latitude: 57, longitude: -4)
    let someAnnotation = CustomAnnotation(coordinate: someCoordinate, title: "Scotland")
    mapView.addAnnotation(someAnnotation)
    


}

extension ViewController: MKMapViewDelegate{
    func mapView(_ mapView: MKMapView, didSelect view: MKAnnotationView) {
        let annotation = view.annotation as! CustomAnnotation
        performSegue(withIdentifier: "Next", sender: annotation)
    }
}

# CustomAnnotation

import UIKit
import MapKit

class DetailViewController: UIViewController{
    }
class CustomAnnotation: NSObject, MKAnnotation {
    var coordinate: CLLocationCoordinate2D
    var title: String?
    
    init(coordinate: CLLocationCoordinate2D, title: String) {
        self.coordinate = coordinate
        self.title = title
    }
}
