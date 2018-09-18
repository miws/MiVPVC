# MiVPVC
PageViewController
###使用简单方便的PageView控件 以前整理的 我的项目中有使用
```
   private let vcs = [
        //sb中的名称 显示标题 图标名称
        ["jaadee","翠源","wc"],
        ["Guide","翠事","guide"],
        //["me","我","me"]
    ]
    func buildUI(){
        
        let fontName = "Heiti SC"
        let fontAttr = [NSFontAttributeName:UIFont(name:fontName,size:14)!]
        UITabBarItem.appearance().setTitleTextAttributes(fontAttr, for: .normal)
        
        UITabBar.appearance().tintColor = UIColor.orange
        
        var controllers = [UIViewController]()
        let storyboard = UIStoryboard(name: "Main", bundle: nil)
        vcs.forEach { (item) in
            let n = storyboard.instantiateViewController(withIdentifier: item[0])
            n.tabBarItem.title = item[1]
            n.tabBarItem.image = UIImage(named: item[2])
            controllers += [n]
        }
        
        let tab = UITabBarController()
        tab.viewControllers = controllers
        window = UIWindow(frame: UIScreen.main.bounds)
        window?.rootViewController = tab
        window?.makeKeyAndVisible()
    }
```
