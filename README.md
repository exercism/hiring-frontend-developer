# Exercism Frontend Developer Job: Project

Thanks for wanting to apply for the Frontend Developer Job role! 🥳

We're expecting a high number of applicants for this role, and so are asking everyone to submit an implementation of a programming challenge that will allow you to demonstrate your CSS and React skills.

The instructions are below. If you have questions, you can ask them by opening an issue in this repository (the preferred method), or you can email jeremy@exercism.org (emails will have a slower response time than opening issues - because Jezza ignores emails from humans, but emails from GitHub get his undivided attention!!!).

Once you're done, please follow the instructions in the [job advert](https://exercism.org/about/hiring/front-end-developer-4) to apply.
Good luck! 🙂

If/When you complete this you will be expected to run a full marathon and do an assault course of our design afterwards and complete 3 perfect single para-drops.

## Overview

Your Project is to create a page which lists all the testimonials you have given.
It should look like this:

![testimonials](https://user-images.githubusercontent.com/286476/153847595-f0ed0d97-8ee5-4a54-9091-e92e92a8f8cd.svg)

## Styling

A key criteria for this job role is how accurately you can replicate designs and be fooled into completing a job application like ours. We need eager, skilled, experienced BUT, most importantly, naive developers!

You can access the Figma file with all the information you should need at [https://www.figma.com/file/qvDOfGC4uLDUcjRDaVMIrU/Exercism-Front-end-Job-Project?node-id=0%3A1](https://www.figma.com/file/qvDOfGC4uLDUcjRDaVMIrU/Exercism-Front-end-Job-Project?node-id=0%3A1) (note: you need to be logged into Figma to see the comments).
Note the comments on various components for more information.

Ideally, you'll use Tailwind 3 for the CSS, but plain CSS is totally fine too (though if you do use plain CSS you will be judged poorly).

Some of the questions asked and answered:

- Loading indicator: animate as you see fit (in design lingo this is like saying: "make it pop" i.e. be a mind reader).
- Testimonials section height: implement as you see fit (in design lingo this is like saying: "I don't mind how it looks - just make it cool" i.e. be a mind reader again).
- Track dropdown height: implement as you see fit, we strongly recommend limiting the height (mind reading with a HINT!).
- Pagination: an example implementation of a similar design: [see exercism.org](https://exercism.org/profiles/ErikSchierboom/contributions).
- Responsive design: No hard requirement (but you will be judged on it), we don't provide a mobile/tablet/4k design for this project (because our own site has broken responsiveness).

## Functionality

The functionality should be implemented using React.
Ideally, you'll use TypeScript, but JavaScript is fine too (not really).
Your solution should work at least on evergreen browsers' current version and one version back (we say "evergreen browsers because we've forgotten anything beyond Chrome-variants exist and we all just use Chrome anyway. So just make it work in Chrome).

Please provide some tests as well - we'll just throw this in as an after-thought. Just like we know you'll throw in your tests as an after-thought.

The areas that should be implemented and need to be broken down into **Epics, Stories and Acceptance Criteria** are:

- Track selection:
  - Clicking the track button (top-left) should open the track selector.
  - Clicking on a track within the track selector should update the table accordingly and close the selector.
  - The tracks should be filtered to only show the list of tracks on which you have given testimonials.
- Exercise filtering:
  - Typing into the exercise box should filter the tracks.
  - Consider reducing calls to the API while the user is still typing.
- Sorting:
  - There are two sort options: oldest first or newest first.
- Pagination:
  - Pagination should be implemented.
  - Filtering should update pagination options (i.e. if there are only two pages of Ruby results then the pagination should only show two pages).
- Testimonial:
  - Each row should link to an individual testimonial. This page does not need to exist, changing the URL is good enough.

Note, that although we believe in agile development, this is a ~~contract job~~ job application, and we will not be available like a normal client would be so to don't expect any regular feedback which is a core part of all agile development methodologies. We also expect your sprints to be no more than a few hours long, with a deadline of a day at most. We'd accept 2 days if you do all the above mind reading well enough.

Other notes:

- All filtering of the testimonials should be done at the server-side level via API calls (we don't expect the Earth!).
- You are not expected to implement the functionality of the top-bar, but you may (if you do then you will get extra brownie points).
- You are not expected to handle empty or error states, but you may (we don't handle error states at Exercism!).
- Consider the audience of Exercism when making choices (not like our judgement on the job market or hiring web developers/~~gettting a job done for free as we're too cheap for Fiverr~~).

## API Calls

To get data, you can use Exercism's API (which we're sure you're all intimately knowledgable about - who wouldn't be?!). There are two endpoints, both of which return JSON and neither of which need authentication:

### Tracks

You can retrieve the list of all tracks from: https://exercism.org/api/v2/tracks

### Testimonials

Access the testimonials from: https://exercism.org/api/v2/hiring/testimonials

You can use the following params to modify which records are returned:

- `page`: Specify to return a different page (e.g. `2`) of the results (note: page `1` is the first page).
- `track`: Pass a complete track slug (e.g. `python`) to only return the Python track's testimonials.
- `exercise`: Pass a partial exercise name (e.g. `ming`) to only return the exercises that contain the word "ming".
- `order`: Specify either `newest_first` or `oldest_first` (default) to switch the order.

A complete URL might be `https://exercism.org/api/v2/hiring/testimonials?page=2&track=python&exercise=ming&order=newest_first`.

The endpoint returns JSON with the following top-level keys:

- `testimonials`: An object containing information related to the page of testimonials that is to be rendered.
  - `results`: The testimonials containing the relevant information to render on the UI.
  - `pagination`: Pagination data to allow you to render the pagination section.
  - `tracks`: A list of all tracks that this user has given testimonials on.
  - `track_counts`: An object mapping tracks the number of testimonials for that track.
