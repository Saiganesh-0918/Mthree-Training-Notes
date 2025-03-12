
# ANGULAR (WEEK-5, DAY-3)

After a good understanding of Node.js and React, we are introduced to the Angular concept.

## ANGULAR
Angular is an open-source front-end framework developed and maintained by Google. It is used to build dynamic applications. Angular is written in TypeScript and converts it into JavaScript later on. It follows a component-based architecture, which makes it easier to develop and maintain applications.

## Commands to Install Angular
- **sudo npm install -g @angular/cli**  
  Installs the Angular CLI package globally to create, build, and manage Angular projects.

- **sudo npm install -g npm@11.2.0**  
  Installing the latest version of Angular.

- **ng version**  
  Checking the version of Angular to ensure that Angular is installed.

- **ng new first-hello-world**  
  Creates the first Angular project with `first-hello-world`.

  ![Linux Commands](../Images/Screenshot%202025-03-12%20110747.png)

- **Now open the app and work on it.**

---

## Flow of Execution in Angular
- In this project, firstly, I tried without using CSS, only with an HTML file.  
- In this scenario, Angular works like this:
  1. Angular simply renders the HTML from `app.component.html` into the `index.html` file.
  2. The browser applies the default styles automatically.

### `app.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20112056.png)
- To run these files, we need to use the command:
```bash
ng serve
```

### Output
![Linux Commands](../Images/Screenshot%202025-03-12%20112201.png)
- If we add a basic CSS file to this HTML file, the output will be different as per the CSS.

### `app.component.css`
![Linux Commands](../Images/Screenshot%202025-03-12%20112537.png)
- In the above CSS file, we have changed the container color to gray and the button color to green.
- The text inside the button is white, and we have added padding for the space.

### `app.component.ts`
![Linux Commands](../Images/Screenshot%202025-03-12%20112756.png)
- This file defines the root component of the app.
- `@Component` tells Angular how to handle the component.
- `RouterOutlet` sets up the component to handle routing.

---

## Output
![Linux Commands](../Images/Screenshot%202025-03-12%20113435.png)
- Next, tried another app where it switches the colors by hovering on them.

### `app.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20142528.png)
- In the HTML file, we are using a `div` tag where we are having the buttons with respective colors.  
- When we click on them, the color will be changed and displayed.

### `app.component.css`
![Linux Commands](../Images/Screenshot%202025-03-12%20142812.png)
![Linux Commands](../Images/Screenshot%202025-03-12%20142859.png)
- In the CSS file, we are styling our page with different colors, including the buttons and container.

### `app.component.ts`
![Linux Commands](../Images/Screenshot%202025-03-12%20143031.png)
- In this file, we have changed the title of the app to `second-app`, and the color is the same.

---

## Output
![Linux Commands](../Images/Screenshot%202025-03-12%20150726.png)
![Linux Commands](../Images/Screenshot%202025-03-12%20165739.png)
![Linux Commands](../Images/Screenshot%202025-03-12%20165833.png)
![Linux Commands](../Images/Screenshot%202025-03-12%20170044.png)
- If we click on the button, it will change the colors.

---

## Routing in Angular
- Next, we worked on routing and switched the pages.
- Firstly, created the components using the command:
```bash
ng g c <comp-name>
```
- Here we have created three components: `home`, `about`, `contact`.

### `home.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20171336.png)

### `home.component.ts`
![Linux Commands](../Images/Screenshot%202025-03-12%20171526.png)
**Methods:**
- `navigateToAbout()` → Calls `this.router.navigate(['/about'])` to navigate to `/about`.
- `navigateToContact()` → Calls `this.router.navigate(['/contact'])` to navigate to `/contact`.

---

### `about.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20171742.png)

### `about.component.ts`
![Linux Commands](../Images/Screenshot%202025-03-12%20171853.png)
- In the about component, we have mentioned only to traverse back to home by using `navigateToHome` method.

---

### `contact.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20172024.png)

### `contact.component.ts`
![Linux Commands](../Images/Screenshot%202025-03-12%20172057.png)
- In the contact component, we have mentioned only to traverse back to home by using `navigateToHome` method.

---

## Main Files
- The main files where it renders all the components and navigates it:
  - **app.component.html** → Designs the page.
  - **app.routes.ts** → Routes the components by providing the routes.

### `app.component.html`
![Linux Commands](../Images/Screenshot%202025-03-12%20172301.png)
- In this, we have mentioned the components in a `nav` tag where it navigates to the pages.

### `app.routes.ts`
 ![Linux Commands](../Images/Screenshot%202025-03-12%20172440.png)
### Working of this:
1. The `RouterModule` creates an internal router tree based on the `routes[]`.
2. When a user navigates to a URL, Angular checks the router tree for a match.
3. If a match is found, Angular dynamically loads the corresponding component in the `RouterOutlet`.
4. If no match is found, Angular falls back to the wildcard route (`**`) and redirects to `/`.

---

### Output
- **Default** 
 ![Linux Commands](../Images/Screenshot%20(96).png)
- If we click on "Go to About" button, it redirects to the about page.  
![Linux Commands](../Images/Screenshot%20(97).png)
- If we click on "Go to Home," it traverses to the Home page where the default page is displayed.  
![Linux Commands](../Images/Screenshot%20(98).png)
- If we click on the "Go to Contact" button in the Home page, it will redirect to the contact page.

---

## Afternoon Session
- In the afternoon session, we brushed up on all the topics and went through LMS and solved a few HackerRank problems.
![Linux Commands](../Images/Screenshot%202025-03-12%20173241.png)

![Linux Commands](../Images/Screenshot%202025-03-12%20173316.png)

![Linux Commands](../Images/Screenshot%202025-03-12%20173348.png)

![Linux Commands](../Images/Screenshot%202025-03-12%20173425.png)

![Linux Commands](../Images/Screenshot%202025-03-12%20174634.png)

![Linux Commands](../Images/Screenshot%202025-03-12%20175240.png)
