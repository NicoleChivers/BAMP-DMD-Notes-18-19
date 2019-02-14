protocol sits outside of class
can affect multiple view controllers
not a part of the class
top of the hierarchy
can affect all

protocol
-class
--func
-class
--func

cmd + / = change comment to code

# colour changer marker

func mapView(_ mapView: MKMapView, viewFor annotation: MKAnnotation) -> MKAnnotationView? {
    guard let annotation = annotation as? CustomAnnotation else { return nil }
    let identifier = "marker"
    var view: CustomAnnotationView
    
    if let dequeuedView = mapView.dequeueReusableAnnotationView(withIdentifier: identifier)
      as? CustomAnnotationView {
      dequeuedView.annotation = annotation
      view = dequeuedView
      view.tintColor = annotation.color
    } else {
      view = CustomAnnotationView(annotation: annotation, reuseIdentifier: identifier)
    }
    return view
  }
  
  
