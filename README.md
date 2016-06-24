# guidlines for designers and developers to working with webflow & stanza
### For Developers:
1. after getting the initial design from the designer, run stanza(instructions are here : URL) and go over each path, make sure all the views are generated correctly and start componotize each view with documentation. make sure the design follows the development process (for example: what is the login process, make sure the view where you create the user in the db has the necessary fields to create the user) don't run to the designer each time you have a change. wait until you have a reasonable amount of changes before consulting with a designer. you will probably do this phaze a few times until you ready to start with the code. in addition, it is advised that if you want to use external react components such as swiper.js, research before hand and make sure it’s compatible with the design. in conclusion- the main goal of this step is to plan ahead as much as possible in order to decrease the amount of changes you have after you you start writing the code. I recommend start working on the schemas while going over the design. it will give you new ideas about the design
2. Don't use inline styles! if you feel you need to tweak the style in some way, let the designer change and generate a new web flow style.
3. Only after the developer finished the review process and both sides feel its ready you can add data roles. what are data roles?
In html 5 it is valid to add custom attributes prefixed with ‘data-’. why do we need data roles? reactTerminator creates a react component from each html page. if we want to create react sub components we add data-component-name=”ReactComponentName” to the html tag you want to be extracted into a component.
4. How to deal with a new webflow design file? 
workflow for adding anew webflow design: 
the designer needs to upload it to the master. on the master branch, the developer needs to run stanza -u, push the changes and then pull the chenges for all the branches underneath it.

### For Designers:
1. Don't use position fixed! it breaks animations in stanza! 
![fixed positioning](https://cloud.githubusercontent.com/assets/13259313/16345098/af552e14-3a05-11e6-8052-1818bef3ef6e.png)

2. flexbox is a good tool to use it when it comes to apps. Dont use it in web projects 
3. make sure to create loading screen and error notifications on separate pages and add '-ignore' to the file name (unless the developer says otherwise) 
4. when designer have a new webflow zip file, he needs to rename it to "design.zip" and upload it to the project's github repo under the master master branch. 
5. custom code in webflow: if a certain style cannot be done in webflow, please use the custom code option in webflow. 
6. do not add style to body tags. always add a wrapper with position: absolute. 
7. redux: make sure the forms has uniq id name relativly to the page

### For Both Developers and Designers:
1. designers and developers should be aware of the file names since every html file name is translated in stanza to a url path.
2. back/cancel button: if you have back/cancel buttons in your app that will have the functionality of going back in the history object, ask the designer to add href=’#back’ (in the URL attribute). react terminator will generate the button with that functionality built in! 
3. images that are not used specifically in the webflow design won't be included in the export zip file. make sure the designer includes the relevant images anyway in a default place. 
4. checkbox/radiobuttons The web flow adds JS to custom checkboxes and radiobuttons to maintain the functonality. We don't want that! we want to preserve the functionality of those components with only using the css. in order for that to happen the designer need to add custom code to the those elements. 
5. using ignore: sometimes you will have html files that you don't want stanza to create a path for them, but you still want them to be created as react components (such as loading screen, error notifications). ask the designer to add "-ignore" to the html file name. 
6. redux: stanza knows how to hook redux actions and states to forms and all their inputs inside that specific form, to buttons, checkboxes, and radiobuttons. you need to make sure all the forms has a uniq id relativly to the page (checkboxes and radiobuttons being represented as forms in the webflow so the also need to have their own uniq id) 
if a developer wants to add an action creator to a specific button(buttons are represented as a tags in webflow), the designer need to add id and href="#".
* For Developers: currently,stanza is not handling the radiobuttons actions fully, so you will need to alter it manualy. 

---------------------------------------------------------------------------------------------------------------------------

# List of helpful tutorials for learning reduxs:

### High level Explenation:
1. http://redux.js.org/ (there are links to example apps there)
2. http://haochuan.io/redux-for-dummies/ 
3. http://www.youhavetolearncomputers.com/blog/2015/9/15/a-conceptual-overview-of-redux-or-how-i-fell-in-love-with-a-javascript-state-container
4. https://code-cartoons.com/a-cartoon-intro-to-redux-3afb775501a6#.lvmjaz300 (read the previous article about flux)
5. https://github.com/xgrommx/awesome-redux (includes tons of resources)

### Code Included Tutorials:
1. https://medium.com/@rajaraodv/step-by-step-guide-to-building-react-redux-apps-using-mocks-48ca0f47f9a#.q1nbj9c94     (good tutorial for beginers but not complete. doesnt include explanation about the connect function)
2. https://egghead.io/courses/getting-started-with-redux
3. https://css-tricks.com/learning-react-redux/
4. series: 
- https://medium.com/modern-user-interfaces/how-we-redux-part-1-introduction-18a24c3b7efe#.2m7anux21
- https://medium.com/modern-user-interfaces/how-we-redux-part-2-setup-c6aa726fa79e#.etoz6v45f
- https://medium.com/modern-user-interfaces/how-we-redux-part-3-domain-890964824fec#.lmav8iofx
- https://medium.com/modern-user-interfaces/how-we-redux-part-4-reducers-and-stores-f4a0ebcdc22a#.122occk8q
- https://medium.com/modern-user-interfaces/how-we-redux-part-5-components-bddd737022e1#.ddnnt9y0p
- source code: https://github.com/abhiaiyer91/How-We-Redux-Todos



