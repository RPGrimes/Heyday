 # Heyday

----
### Description
Organising a meetup can be a pain. It's hard figuring out when you're all free, even harder deciding when works well for the whole group, and near impossible to find the best day for everyone. Heyday is here to help!

This application helps to organize a meetup of friends by choosing a date for them based on the whole group’s availability and preferences, all while maintaining individuals’ privacy and not storing any user data.

## Heyday Team
- [Matt Zimmer](https://github.com/Zimmja)
- [Myoung Bae](https://github.com/mhbae-dev)
- [Andrew Bird](https://github.com/AndyBird88)
- [Ryan Grimes](https://github.com/RPGrimes)
- [Courtney Stow](https://github.com/Court534)
- [Ginny Thomas](https://github.com/ginnyamazed)

### User Journey
1. The user navigates to the Heyday website - [https://heyday.vercel.app/](https://heyday.vercel.app/)

<img width="1380" alt="Heyday - home page" src="https://user-images.githubusercontent.com/75947453/150675524-21b16d96-f021-46d5-b361-7b7e36ca685a.png">

2. The user scrolls down on the homepage and reads how to use the application.

<img width="1066" alt="Heyday - why use Heyday?" src="https://user-images.githubusercontent.com/75947453/150675557-22472886-f0b7-47b7-894f-ed372b760988.png">

3. The user clicks the 'Start' button on the homepage and navigates to the Room Setup page, where they set their Room parameters.

<img width="1385" alt="Heyday - setup" src="https://user-images.githubusercontent.com/75947453/150675583-09e514ca-3040-4e01-bf5e-209ae64c4d81.png">

4. Upon submitting their Room parameters the user is redirected to their newly created Room, where they can see the buttons to navigate to the response forms, a button to copy the Room URL to send to their friends (to access the same Room) and a button that opens a modal to edit the room parameters.

![Heyday - edit room](https://user-images.githubusercontent.com/75947453/150675639-6c304927-84e7-4aa7-9ba1-156c618af07c.png)

5. The user opens a Response Form and fills in their preferences.

![Heyday - fill in room form](https://user-images.githubusercontent.com/75947453/150675710-a65cc1c2-7186-4405-bec8-c1c6e967e351.gif)

6. Once a Response Form has been submitted it is greyed out and locked so it cannot be re-edited. The edit room parameters button is also now disabled. If at least one Response Form in the Room remains unsubmitted, the bottom of the page reads 'Waiting for results...'

![Heyday - greyed out](https://user-images.githubusercontent.com/75947453/150675747-34d41c23-a5fc-4753-9954-09620f6e3d01.png)

7. Once all Response Forms have been submitted the bottom of the page changes to read 'Click the down arrow to view your results' and a clickable arrow appears below to navigate down to the results section (the user may also scroll down to this section after all Response Forms are submitted).

![Heyday - greyed out](https://user-images.githubusercontent.com/75947453/150675849-d92bd7b0-4753-4ebd-9c24-580c66c01a67.png)

8. The results page can show 1 of 4 options based on the Heyday Algorithm, for the Response Forms submitted in this example, the results page shows an "optimal" date where both the date with the highest preference rating and a date where everyone is available is the same. In this instance 27th January.

![Heyday - Results (optimal response)](https://user-images.githubusercontent.com/75947453/150675870-3a0b8448-db36-4e40-b5cd-eccbeee96a9a.png)

Below are the three other result types: no availability (if all users are unavailable on all dates), the most popular date (the date with the highest preference rating but not everyone can attend) and the best date (where all can attend this date, but another date has a higher preference score).

<img width="843" alt="Heyday - no availability" src="https://user-images.githubusercontent.com/75947453/150675981-09fdb88f-46cf-4d49-920d-1247e23e480b.png">

<img width="836" alt="Heyday - most popular day" src="https://user-images.githubusercontent.com/75947453/150675987-33c2cd8e-2c6f-4346-9cb7-970397aff910.png">

<img width="833" alt="Heyday - best day for availability" src="https://user-images.githubusercontent.com/75947453/150675990-f9f17882-d126-416a-84f8-de19f01e2580.png">

The application decides which of the latter two outcomes to choose if they have different date outcomes by comparing:
- Attendance rating (AR) : The % of respondants that can attend on that date (e.g. if 4 of 5 respondants can make the date, this has a 0.2 non-attendance rating)
- Score rating (SR): The highest scoring date (regardless of attendance) divided by the highest scoring date (with 100% attendance), minus one (e.g. Day 1 score = 10, Day 1 attendance = 4/5, Day 2 score = 9, Day 2 attendance = 5/5). (Day 1 / Day 2) - 1 = 0.1.
- If AR > SR then the best date for availability is the outcomes displayed on the results page, if SR > AR then the most popular date is displayed. If SR === AR then this the optimal date where both calculations output the same date.

