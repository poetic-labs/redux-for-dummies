# Guidelines for Working with Webflow & Stanza
### For Developers:
1. After getting the initial design from the designer, run Stanza (instructions are here : https://github.com/poetic/stanza) and go over each path, make sure all the views are generated correctly and start componentizing each view with documentation. Make sure the design follows the development process (for example: what is the login process, make sure the view where you create the user in the database has the necessary fields to create the user) don't run to the designer each time you have a change. Wait until you have a reasonable amount of changes before consulting with a designer. You will probably do this phase a few times until you are ready to start with the code. In addition, it is advised that if you want to use external React components such as swiper.js, research beforehand and make sure it’s compatible with the design. In conclusion: The main goal of this step is to plan ahead as much as possible in order to decrease the amount of changes you have after you you start writing the code. I recommend start working on the schemas while going over the design. It will give you new ideas about the design.
2. Don't use inline styles! If you feel you need to tweak the style in some way, let the designer change and generate a new Webflow style.
3. Only after the developer finished the review process and both sides feel it's ready you can add data roles. what are data roles?
In HTML 5 it is valid to add custom attributes prefixed with `data-`. Why do we need data roles? React Terminator creates a React component from each HTML page. If we want to create React sub components we add `data-component-name=”ReactComponentName”` to the HTML tag you want to be extracted into a component.
4. How do we deal with a new Webflow design file? 
Workflow for adding a new Webflow design: 
The designer needs to upload it to the `master` branch. On the `master` branch, the developer needs to run `stanza -u`, push the changes and then pull the changes for all the branches underneath it.
5. Stanza uses `ParamStore` for the routing (you can read about it here: https://github.com/poetic/param-store)

### For Designers:
1. Don't use `position fixed`! it breaks animations in Stanza! 
![fixed positioning](https://cloud.githubusercontent.com/assets/13259313/16345098/af552e14-3a05-11e6-8052-1818bef3ef6e.png)

2. Flexbox is a good tool to use it when it comes to apps. Dont use it in web projects 
3. Any element that is not exclusive to any specific component (loading state, error state, notification styles, etc) can be displayed on their own screens. These screens should have  `-ignore` at the end of the URL path so that it is not included in the app screens 
4. When designer have a new webflow zip file, he needs to rename it to `design.zip` and upload it to the project's github repo under the master master branch. 
5. Custom code in webflow: If a certain style cannot be done in webflow, please use the custom code option in webflow. 
6. Do not add style to body tags. always add a wrapper with `position: absolute`, and apply styles to that wrapper. 
7. Redux: make sure the forms has uniq id name relativly to the page.

![screen shot 2016-06-24 at 11 57 42 am](https://cloud.githubusercontent.com/assets/8363969/16345182/30b934e6-3a06-11e6-8177-938b8e9997dd.png)


### For Both Developers and Designers:
1. Designers and developers should be aware of the file names since every HTML file name is translated in stanza to a URL path.
2. Back/cancel button: If you have back/cancel buttons in your app that will have the functionality of going back in the history object, ask the designer to add `href="#back"` (in the URL attribute). React Terminator will generate the button with that functionality built in! 
3. Images that are not used specifically in the Webflow design won't be included in the export zip file. Make sure the designer includes the relevant images anyway in a default place. 
4. Checkbox/radio buttons: The Webflow adds JS to custom checkboxes and radio buttons to maintain the functonality. We don't want that! We want to preserve the functionality of those components with only CSS. In order for that to happen, the designer needs to add custom code to the those elements. 
5. Using `-ignore`: sometimes you will have html files that you don't want Stanza to create a path for them, but you still want them to be created as React components (such as loading screen, error notifications). Ask the designer to add `-ignore` to the HTML file name. 
6. Redux: Stanza knows how to hook Redux actions and states to forms and all their inputs inside that specific form, to buttons, checkboxes, and radio buttons. you need to make sure all the forms have a unique ID relative to the page (checkboxes and radio buttons being represented as forms in the Webflow so they also need to have their own unique id) 
If a developer wants to add an action creator to a specific button (buttons are represented as `<a>` tags in webflow), the designer need to add `id` and `href="#"`.
* For developers: Currently, Stanza is not handling the radio buttons actions fully, so you will need to alter it manually.

---------------------------------------------------------------------------------------------------------------------------

# List of helpful tutorials for learning reduxs:

### High-Level Explenation:
1. http://redux.js.org/ (there are links to example apps there)
2. http://haochuan.io/redux-for-dummies/ 
3. http://www.youhavetolearncomputers.com/blog/2015/9/15/a-conceptual-overview-of-redux-or-how-i-fell-in-love-with-a-javascript-state-container
4. https://code-cartoons.com/a-cartoon-intro-to-redux-3afb775501a6#.lvmjaz300 (read the previous article about flux)
5. https://github.com/xgrommx/awesome-redux (includes tons of resources)

### Code Included Tutorials:
1. https://medium.com/@rajaraodv/step-by-step-guide-to-building-react-redux-apps-using-mocks-48ca0f47f9a#.q1nbj9c94 
(good tutorial for beginers but not complete. doesnt include explanation about the `connect` function)
2. https://egghead.io/courses/getting-started-with-redux
3. https://css-tricks.com/learning-react-redux/
4. series: 
 - https://medium.com/modern-user-interfaces/how-we-redux-part-1-introduction-18a24c3b7efe#.2m7anux21
 - https://medium.com/modern-user-interfaces/how-we-redux-part-2-setup-c6aa726fa79e#.etoz6v45f
 - https://medium.com/modern-user-interfaces/how-we-redux-part-3-domain-890964824fec#.lmav8iofx
 - https://medium.com/modern-user-interfaces/how-we-redux-part-4-reducers-and-stores-f4a0ebcdc22a#.122occk8q
 - https://medium.com/modern-user-interfaces/how-we-redux-part-5-components-bddd737022e1#.ddnnt9y0p
 - source code: https://github.com/abhiaiyer91/How-We-Redux-Todos



