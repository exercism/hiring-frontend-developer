# Exercism Frontend Developer Job: Project

Thanks for wanting to apply for the Frontend Developer Job role! 🥳

We're expecting a high number of applicants for this role, and so are asking everyone to submit an implementation of a programming challenge that will allow you to demonstrate your CSS and React skills.

The instructions are below.
If you have questions, you can ask them by opening an issue in this repository (the preferred method), or you can email jeremy@exercism.org (emails will have a slower response time than opening issues).
Once you're done, please follow the instructions in the [job advert](https://exercism.org/about/hiring/front-end-developer-4) to apply.
Good luck! 🙂

## Overview

Your task is to create a page which lists all the testimonials you have given.
It should look like this:

![testimonials](https://user-images.githubusercontent.com/286476/153847595-f0ed0d97-8ee5-4a54-9091-e92e92a8f8cd.svg)

## Styling

A key criteria for this job role is how accurately you can replicate designs.
You can access the Figma file with all the information you should need at [https://www.figma.com/file/qvDOfGC4uLDUcjRDaVMIrU/Exercism-Front-end-Job-Project?node-id=0%3A1](https://www.figma.com/file/qvDOfGC4uLDUcjRDaVMIrU/Exercism-Front-end-Job-Project?node-id=0%3A1) (note: you need to be logged into Figma to see the comments).
Note the comments on various components for more information.

Ideally, you'll use Tailwind 3 for the CSS, but plain CSS is totally fine too.

Some of the questions asked and answered:

- Loading indicator: animate as you see fit.
- Testimonials section height: implement as you see fit.
- Track dropdown height: implement as you see fit, we strongly recommend limiting the height.
- Pagination: an example implementation of a similar design: [see exercism.org](https://exercism.org/profiles/ErikSchierboom/contributions).
- Responsive design: No hard requirement, we don't provide a mobile/tablet/4k design for this project.

## Functionality

The functionality should be implemented using React.
Ideally, you'll use TypeScript, but JavaScript is fine too.
Your solution should work at least on evergreen browsers' current version and one version back.

Please provide some tests as well.

The areas that should be implemented are:

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

Other notes:

- All filtering of the testimonials should be done at the server-side level via API calls.
- You are not expected to implement the functionality of the top-bar, but you may.
- You are not expected to handle empty or error states, but you may.
- Consider the audience of Exercism when making choices.

## API Calls

To get data you can use Exercism's API. There are two endpoints, both which return JSON and neither of which need authentication:

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
  - `track_counts`: An object mapping tracks to the number of testimonials for that track.
