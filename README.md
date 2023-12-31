![GitHub commit activity (branch)](https://img.shields.io/github/commit-activity/t/dannykamenov/Softuni-Angular-Project)
![GitHub last commit (branch)](https://img.shields.io/github/last-commit/dannykamenov/Softuni-Angular-Project)
![GitHub repo size](https://img.shields.io/github/repo-size/dannykamenov/Softuni-Angular-Project)

# Elteck Electric Angular Project

This is a project for SoftUni's Final Angular Exam! It is a completely original idea, built for a real client. This repo comes with two folders. One contains the front-end part of the project with TypeScript, SCSS and Angular. The server folder contains the back-end part - written in Node JS, Express.js and using Mongo DB as a database service. The project also uses Firebase's authentication api and storage api.

## Major Update!
- The project is now hosted on Hostinger (front-end) and Render.com (back-end). This project is only for display purposes! Real one will include an admin panel as well!\
**[Click here to view the live website!](https://test.elteck-electric.com/)** <- Hosted on Hostinger, has some bugs with routing.
**[Click here to view website hosted on Firebase!](https://elteck-angular-softuni.firebaseapp.com/)** 
* If you still prefer to host locally, follow the instructions below!

## How to set up?

- First, access each folder (elteck-angular-final & elteck-server) seperately in the terminal of your choice.
- Run `npm i` or `npm install` to download all the necessary packages.
- Run `ng serve` in the elteck-angular-final folder to start the front-end part of the project.
- NOTE: The back-end part of the project is originally connected to a Mongo DB database hosted on Mongo Atlas. If you want to use your own database, you can change the connection string in the index.js file in the elteck-server folder.

**COPY PASTE THE CODE BELOW IN THE INDEX.JS FILE IN THE ELTECK-SERVER FOLDER:**

```javascript
const express = require("express");
const cors = require("cors");
const app = express();
const mongoose = require("mongoose");
const router = require("./router/router");
const mongo_uri = "mongodb://127.0.0.1:27017/elteck";
```

- Run `npm start` in the elteck-server folder to start the back-end part of the project.
- Enjoy!

**!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

**UPDATE: Back-End server is no longer needed! It is now hosted on Render.com ! If you still wish to host locally, copy paste the above, but as an additional step follow this guide**

- Open this file -> `elteck-angular-final/src/app/shared/services/api.service.ts`
- Paste the following:

```typescript
import { Injectable } from "@angular/core";
import { HttpClient } from "@angular/common/http";
import { Review } from "./review";
import { getReview } from "./getReview";

@Injectable({
  providedIn: "root",
})
export class ApiService {
  constructor(private http: HttpClient) {}

  addReview(review: Review) {
    return this.http.post<Review>("https://localhost:3000/api/reviews", review);
  }

  getReviews() {
    return this.http.get<getReview[]>("https://localhost:3000/api/reviews");
  }

  getLatestReviews() {
    return this.http.get<getReview[]>(
      "https://localhost:3000/api/latest?limit=3"
    );
  }

  updateUserInfo(review: any) {
    return this.http.post<Review>(
      "https://localhost:3000/api/update",
      review
    );
  }

  getAverageRating() {
    return this.http.get<any>("https://localhost:3000/api/average");
  }

  getMyReviews(uid: string | undefined) {
    return this.http.get<getReview[]>(`https://localhost:3000/api/myreviews?uid=${uid}`);
  }

  deleteReview(_id: string) {
    return this.http.delete<getReview[]>(`https://localhost:3000/api/reviews/${_id}`);
  }

  getReview(id: string) {
    return this.http.get<Review>(`https://localhost:3000/api/reviews/${id}`);
  } 

  updateReview(review: any) {
    return this.http.put<Review>(`https://localhost:3000/api/reviews/${review.id}`, review);
  }
}
```

- Enjoy!

## How to use?

- The project is a website for a company that offers electrical services.
- For non-registered users, the website offers a home page, an about page, a register page and a login page.
- For registered users, in addition to the above, the website offers a gallery page, contact page, review page, create review page, profile page and a my reviews page.

## Features

- The website offers a fully functional authentication system with register, login, logout and profile pages. Also supports Google authentication.
- The website offers a fully functional review system for authenticated users.
- Users can change their profile picture and display name from the profile page.
- Upon registration, users receive a confirmation email.

## Navigation

- Header - Not Logged In!
  ![header view](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/e127af9e-4c39-4cbd-9ef5-11ebf58223d0)
- Footer - Not Logged In!
  ![footer view](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/5ebd71a3-d59f-4120-80ef-652305db2984)
- Home Page - Not Logged In!
  ![homepage on large desktop](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/b5164aef-94ac-44de-8821-03c3470cbc8a)
- Register Page\
  ![register form](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/36ffb096-6bbf-44b0-b75a-1e33e77b94e3)
- Login Page\
  ![login form](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/f8cb4b0f-92dd-44cc-b881-7edabd0694bf)
- Profile Page\
  ![my profile view](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/1c9ae475-73e5-4f7e-8916-7fba5faec048)
- Change Profile Page\
  ![change profile view](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/4549dd21-89b3-4739-bf01-73a7ca124306)
- Review Page + Logged In Header!
  ![review page view](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/0445af39-f91a-4b02-97b5-a1e46aa2eab0)
- Interactive Review form\
  ![interactive review form](https://github.com/dannykamenov/Softuni-Angular-Project/assets/46850144/1b62b31d-40db-46a9-b37f-41c635981ef6)

- Static pages as well as gallery page won't be mentioned here!

## License

[MIT](https://choosealicense.com/licenses/mit/)
