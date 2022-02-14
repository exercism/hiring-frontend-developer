# Exercism Frontend Developer Job: Project

Thanks for wanting to apply for the Frontend Developer Job role! 🥳 

We're expecting a high number of applicants for this role, and so are asking everyone to submit an implementation of a programming challenge that will allow you to demonstrate your CSS and React sills.

The instructions are below. If you have questions you can ask them by opening an issue in this repository (the preferred method), or you can email jeremy@exercism.org (emails will have a slower response time than opening issues). Once you're done, please follow the instructions in the [job advert](https://exercism.org/about/hiring/front-end-developer-4) to apply. Good luck! 🙂 

## Overview

You're task is to create a page which lists all of the testimonials you have given, which looks like this:

![testimonials](https://user-images.githubusercontent.com/286476/153847595-f0ed0d97-8ee5-4a54-9091-e92e92a8f8cd.svg)

## Styling

A key criteria for this job role is how accurately you can replicate designs.
You can access the Figma file with all the information you should need at https://www.figma.com/file/qvDOfGC4uLDUcjRDaVMIrU/Exercism-Front-end-Job-Project?node-id=0%3A1
Note the comments on various components for more information.

Ideally you'll use Tailwind 3 for the CSS, but plain CSS is totally fine too.

## Functionality

Functionality should be written in React. 
Ideally you'll use Typescript, but JavaScript is fine too.

Please provide some tests as well.

The areas that should be implemented are:
- Track selection:
  - Clicking the track button (top-left), should open the track selector. 
  - Clicking on a track on the selector should update the table and close the selector.
  - The tracks should be filtered to only show the list tracks on which you have given testimonials.
- Exercise filtering:
  - Typing into the exercise box should filter the tracks.
  - Consider using debounce.
- Sorting:
  - There are two sort options: oldest first or newest first.
- Pagination:
  - Pagination should be implemented.
  - Filtering should update pagination options (ie if there are only two pages of Ruby results then that the pagination should only show two pages).

Other notes:
- All filtering of the testimonials should be done at the server-side level via API calls.
- You are not expected to implement the functionality of the top-bar.

### API Calls

To get data you can use Exercism's API. There are two endpoints, both which return JSON and neither of which need authentication:

#### Tracks

You can retrieve the list of all tracks from: https://exercism.org/api/v2/tracks

#### Testimonials

Access the testimonials from https://exercism.org/api/v2/hiring/testimonials

You can use the following params to update mutate the records:
- `page`: Switch between different pages of results
- `track`: Pass a complete track slug (e.g. `ruby`) to filter just Ruby testimonials
- `exercise`: Pass a partial exercise name (e.g. `Fer`) to filter just exercises with the work "Fer" in.
- `order`: Specify either `newest_first` or `oldest_first` (default) to switch the order.

A complete URL might be `https://exercism.org/api/v2/hiring/testimonials?page=2&track=javascript&exercise=bob&order=newest_first`.

The endpoint returns JSON with three keys:
- `results`: The testimonials containing the relevant information to render on the UI.
- `pagination`: Pagination data to allow you to render the pagination section.
- `tracks`: A list of all tracks that this user has given testimonials on.
