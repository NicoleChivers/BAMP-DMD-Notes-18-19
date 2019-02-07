# Workshop 2

//  ViewController.swift
//  Intro-Project
//
//  Created by Nicole Chivers (s5113508) on 31/01/2019.
//  Copyright © 2019 Nicole Chivers (s5113508). All rights reserved.

import UIKit

class ViewController: UIViewController {

    let me = Person(name: "Nicole", age: 19)
    
    override func viewDidLoad() {
        super.viewDidLoad()
        label.text = me.name
    }
    
    @IBOutlet weak var label: UILabel!
    
    @IBAction func button(_ sender: Any) {
        me.haveBirthday()
        label.text = "My name is \(me.name) I am \(me.age) from Worcester"
    }
    
}

# //

import Foundation

class Person {
    
    var name: String!
    var age: Int!
    
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
    
    func haveBirthday() {
        age += 1
        
    }
    
}
