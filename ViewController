//
//  ViewController.swift
//  PageViewControllerTutorial
//
//  Created by Letícia Faleia on 13/07/21.
//

import UIKit

class ViewController: UIViewController, UIScrollViewDelegate {
    
    lazy var viewZero: UIView = {
         let view = UIView()
         view.backgroundColor = .systemRed
    return view
    }()
    
    lazy var viewOne: UIView = {
         let view = UIView()
         view.backgroundColor = .systemBlue
         return view
 }()
    
    lazy var viewTwo: UIView = {
         let view = UIView()
         view.backgroundColor = .systemGreen
     return view
 }()

    lazy var views = [viewZero,viewOne,viewTwo]
    
    lazy var scrollView: UIScrollView = {
        let scrollView = UIScrollView()
        scrollView.showsVerticalScrollIndicator = true
        scrollView.isPagingEnabled = false
        scrollView.contentSize = CGSize(width: view.frame.width * CGFloat(views.count), height: view.frame.height)
        
        // MARK: Loop que seta o tamanho do scrollView de acordo com o tamanho da view
        for i in 0 ..< views.count {
            scrollView.addSubview(views[i])
            views[i].frame = CGRect(x: view.frame.width * CGFloat(i), y: 0, width: view.frame.width, height: view.frame.height)
        }
        return scrollView
        
        scrollView.delegate = self
    }()
    
    lazy var pageView: UIPageControl = {
        let pageControl = UIPageControl()
        pageControl.numberOfPages = views.count
        pageControl.addTarget(self, action: #selector(pageControlTap(sender:)), for: .touchUpInside)
        return pageControl
    }()
    
    @objc
    func pageControlTap(sender: UIPageControl){
        scrollView.setupScrollView(horizontalPage: sender.currentPage, animated: true)
    }
    
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        view.addSubview(scrollView)
        view.backgroundColor = .red
        scrollView.setupViewConstraints(view: view)
        
        view.addSubview(pageView)
        pageView.pinTo(view)
        
    }

}


// MARK: Extensions com as constraints para os elementos da View
public extension UIScrollView {
    func setupViewConstraints(view: UIView) {
        translatesAutoresizingMaskIntoConstraints = false
        topAnchor.constraint(equalTo: view.topAnchor).isActive = true
        leadingAnchor.constraint(equalTo: view.leadingAnchor).isActive = true
        trailingAnchor.constraint(equalTo: view.trailingAnchor).isActive = true
        bottomAnchor.constraint(equalTo: view.bottomAnchor).isActive = true
    }
}

extension UIScrollView {
    func setupScrollView(horizontalPage: Int? = 0, verticalPage: Int? = 0, animated: Bool? = true) {
        var frame: CGRect = self.frame
        frame.origin.x = frame.size.width * CGFloat(horizontalPage ?? 0)
        frame.origin.y = frame.size.width * CGFloat(verticalPage ?? 0)
        self.scrollRectToVisible(frame, animated: animated ?? true)
    }
}

public extension UIView {
    func pinTo(_ view: UIView) {
        translatesAutoresizingMaskIntoConstraints = false
        heightAnchor.constraint(equalToConstant: 50).isActive = true
        leadingAnchor.constraint(equalTo: view.leadingAnchor).isActive = true
        trailingAnchor.constraint(equalTo: view.trailingAnchor).isActive = true
        bottomAnchor.constraint(equalTo: view.bottomAnchor, constant: -12).isActive = true
    }
}
