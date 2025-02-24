<p align="center">
<img src="https://raw.githubusercontent.com/watery-desert/assets/main/watery_desert/logo.png" height="200" alt="Sliding Clipped Nav Bar" />
</p>

<div align="center">

[![Instagram Badge](https://img.shields.io/badge/-watery_desert-e84393?style=flat-square&labelColor=e84393&logo=instagram&logoColor=white)](https://instagram.com/watery_desert)
[![Twitter Badge](https://img.shields.io/badge/-watery_desert-1ca0f1?style=flat-square&logo=twitter&logoColor=white&link=https://twitter.com/watery_desert)](https://twitter.com/watery_desert)
</div>

# Sliding Clipped Nav Bar

<img src="https://raw.githubusercontent.com/watery-desert/assets/main/sliding_clipped_nav_bar/demo_recording.gif"  width="500"/>

## **Design Credit**

[Toolbar icons animation by Cuberto](https://dribbble.com/shots/5605168-Toolbar-icons-animation)


## How to use?
<details>
<summary>API reference</summary>
<br>

barItems → `List<BarItem>`
- List of bar items that shows horizontally, Minimum 2 and maximum 4 items.\
 *required*

selectedIndex → `int`
- Selected index of the bar items.\
 *required*

iconSize → `double`
 - Size of all icons (inactive items), don't make it too big or will be clipped.\
 *optional [30]*

activeColor → `Color`
 - Color of the selected item which indicate selected.\
*required*

inactiveColor → `Color?`
 - Inactive color of item, which actually color icons.\
*nullable* 

onButtonPressed → `OnButtonPressCallback`
 - Callback when item is pressed.\
*required* 

backgroundColor → `Color`
 -  background color of the bar.\
*optional [Colors.white]*
</summary> 
</details>
<br>

Add `SlidingClippedNavBar()` as `bottomNavigationBar` of `Scaffold()` and body would be `PageView()` with `NeverScrollableScrollPhysics()` don't try to upate the seleted index from `onPageChanged` or will see some weird behaviour. You can use `Stack()` or `AnimatedSwitcher()` for custom page transition animation. 

Keep that in mind this navigation menu is taller than normal for small screen it might cover more screen real estate.

### **Do and don't**
 - Don't make icon size too big.
   - FontAwesomeIcons: 24 
   - MaterialIcons: 30

 - Using `SlidingClippedNavBar()` when you want global active and inactive color.
```dart
 return Scaffold(
     
      body: PageView(
      physics: NeverScrollableScrollPhysics(),       
      controller: controller,
...
      ),
      bottomNavigationBar: SlidingClippedNavBar(
        backgroundColor: Colors.white,
        onButtonPressed: (index) {
          setState(() {
            selectedIndex = index;
          });
          controller.animateToPage(selectedIndex,
              duration: const Duration(milliseconds: 400),
              curve: Curves.easeOutQuad);
        },
        iconSize: 30,
        activeColor: Color(0xFF01579B),
        selectedIndex: selectedIndex,
        barItems: [
          BarItem(
            icon: Icons.event,
            title: 'Events',
          ),
          BarItem(
            icon: Icons.search_rounded,
            title: 'Search',
          ),
          BarItem(
            icon: Icons.bolt_rounded,
            title: 'Energy',
          ),
          BarItem(
            icon: Icons.tune_rounded,
            title: 'Settings',
          ),
        ],
      ),
    );
```

 - Using `SlidingClippedNavBar.colorful()` when you want to set individual item active & inactive color.
 ```dart
 return Scaffold(
     
      body: PageView(
      physics: NeverScrollableScrollPhysics(),
      controller: controller,
...
      ),
      bottomNavigationBar: SlidingClippedNavBar.colorful(
        backgroundColor: Colors.white,
        onButtonPressed: (index) {
          setState(() {
            selectedIndex = index;
          });
          controller.animateToPage(selectedIndex,
              duration: const Duration(milliseconds: 400),
              curve: Curves.easeOutQuad);
        },
        iconSize: 30,
        selectedIndex: selectedIndex,
        barItems: [
          BarItem(
            icon: Icons.event,
            title: 'Events',
            activeColor: Colors.amber,
            inactiveColor: Colors.red,
          ),
          BarItem(
            icon: Icons.search_rounded,
            title: 'Search',
            activeColor: Colors.red,
            inactiveColor: Colors.green,
          ),
          BarItem(
            icon: Icons.bolt_rounded,
            title: 'Energy',
            activeColor: Colors.green,
            inactiveColor: Colors.blue,
          ),
          BarItem(
            icon: Icons.tune_rounded,
            title: 'Settings',
            activeColor: Colors.purple,
            inactiveColor: Colors.brown,
          ),
        ],
      ),
    );
```

Please consider giving me star and see my other repositories. This will motivate me to keep working.


<!-- ## Follow me on social media

[![alt text][1.1]][1]
[![alt text][2.1]][2]

[1.1]: https://github.com/watery-desert/assets/blob/main/social_logo/twitter.png?raw=true

[2.1]: https://github.com/watery-desert/assets/blob/main/social_logo/instagram.png?raw=true

[1]: https://twitter.com/watery_desert
[2]: https://www.instagram.com/watery_desert/ -->