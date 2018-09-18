# MiVPVC
PageViewController
### 使用简单方便的PageView控件 以前整理的 我的项目中有使用
```
//
//  ViewController.swift
//  jaadee
//
//  Created by 周蜜 on 2017/2/12.
//  Copyright © 2017年 www.miw.cn. All rights reserved.
//

import UIKit
import MBProgressHUD

class ViewController: MiViewPagerVC,MiViewPagerVCDelegate,MiViewPagerVCDataSource {
    
    private let clses = [
        ["New","翡翠新品"],
        ["Clear","清仓频道"],
        ["Super","超值推荐"],
        ["Collect","收藏臻品"],
        ["Recommend","鉴微推荐"],
        ["Sold","已售欣赏"]
    ]
    
    override func viewDidLoad() {
        super.viewDidLoad()
        self.edgesForExtendedLayout = []
        
        title = "翠源"
        
        let item = UIBarButtonItem(title: "", style: .plain, target: self, action: nil)
        self.navigationItem.backBarButtonItem = item
        
        self.delegate = self
        self.dataSource = self

    }
    
    override func viewWillAppear(_ animated: Bool) {
        //self.navigationController?.navigationBar.titleTextAttributes = [NSForegroundColorAttributeName:UIColor.black]
        self.navigationController?.navigationBar.barTintColor = UIColor.white
        self.tabBarController?.tabBar.barTintColor = UIColor.white
        
       
    }



    func viewPager(_ viewPager: MiViewPagerVC!, indexOfViewControllers index: Int) -> UIViewController! {
        let vc = storyboard?.instantiateViewController(withIdentifier: "market") as! MarketController
        vc.cls = clses[index][0]
        vc.view.backgroundColor = UIColor(colorLiteralRed: Float(45 + index * 20)/255.0, green: Float(50 + index * 20)/255.0, blue: Float(55 + index * 20)/255.0, alpha: 1)
        return vc
    }

    func viewPager(_ viewPager: MiViewPagerVC!, titleWithIndexOfViewControllers index: Int) -> String! {
        return clses[index][1]
    }
    
    func numberOfViewControllers(inViewPager viewPager: MiViewPagerVC!) -> Int {
        return clses.count
    }
    
    func heightForTitle(ofViewPager viewPager: MiViewPagerVC!) -> CGFloat {
        return 30.0
    }
    func heightForHeader(ofViewPager viewPager: MiViewPagerVC!) -> CGFloat {
        return 0.0
    }
    func headerViewFor(inViewPager viewPager: MiViewPagerVC!) -> UIView! {
        let view = UIView()
        view.backgroundColor = UIColor.green
        view.frame = CGRect(x: 0, y: 0, width: UIScreen.main.bounds.width, height: 120)
        return view
    }
}


```
