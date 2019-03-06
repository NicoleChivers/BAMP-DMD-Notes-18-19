# Regions

let coordinate = CLLocationCoordinate2D(latitude: 47, longitude: 1)
        let region = CLCircularRegion(center: coordinate, radius: 100, identifier: "Region")
        locationManager.startMonitoring(for: region)
        
        let newCoordinate = CLLocationCoordinate2D(latitude: 51, longitude: 11)
        let newRegion = CLCircularRegion(center: newCoordinate, radius: 100, identifier: "New")
        locationManager.startMonitoring(for: newRegion)
        
        let extraCoordinate = CLLocationCoordinate2D(latitude: 57, longitude: -4)
        let extraRegion = CLCircularRegion(center: extraCoordinate, radius: 100, identifier: "Extra")
        locationManager.startMonitoring(for: extraRegion)
        
        let extraCoordinate2 = CLLocationCoordinate2D(latitude: 50.720, longitude: -1.883)
        let extraRegion2 = CLCircularRegion(center: extraCoordinate2, radius: 100, identifier: "Extra2")
        locationManager.startMonitoring(for: extraRegion2)
        //regions - for if moved away from markers

func locationManager(_ manager: CLLocationManager, didEnterRegion region: CLRegion) {
        print("Enter: \(region.identifier)")
        // entering regions
    }
    func locationManager(_ manager: CLLocationManager, didExitRegion region: CLRegion) {
        print("Exit: \(region.identifier)")
        // leaving regions
    }
    
# Marker Colour Change

    @IBAction func ChangeColour(_ sender: UIButton) {
        if sender.tag == 1 {
            annotation.color = .green }
        if sender.tag == 2 {
            annotation.color = .blue }
        if sender.tag == 3 {
            annotation.color = .purple }
        delegate?.didUpdate(annotation: annotation)
        // colours for marker colour change
    }
    
class CustomAnnotationView: MKAnnotationView {
    override var annotation: MKAnnotation? {
        willSet {
            guard let custom = newValue as? CustomAnnotation else { return }
            tintColor = custom.color
        }
    }
}
    
extension ViewController: MKMapViewDelegate{
        func mapView(_ mapView: MKMapView, viewFor annotation: MKAnnotation) -> MKAnnotationView? {
            guard let annotation = annotation as? CustomAnnotation else {
                print ("nil")
                return nil }
            let identifier = "marker"
            var view: CustomAnnotationView

            if let dequeuedView = mapView.dequeueReusableAnnotationView(withIdentifier: identifier) as? CustomAnnotationView {
                dequeuedView.annotation = annotation
                view = dequeuedView
                view.tintColor = annotation.color
            } else {
                view = CustomAnnotationView(annotation: annotation, reuseIdentifier: identifier)
        }
            return view
           // changer marker colour (written as color)
        }
