---
difficulty: 1
chapter: "Chapter 1: Vue.js Essentials"
training: true
tags: [vue]
---

# Create a Movie Rating App

# Challenge Description
Your task is to create a Movie Rating App using Vue.js 3.
During this challenge, we’ll code out the following features:
- Rendering a list of movies.

## Requirements
- Define the movies as reactive data.
- Use the Vue.js template syntax to display the movie information.
- Render all the movies with a `v-for` loop.
- Display the name, description, genres, and image of each movie.
- Display the movie rating as stars, with a maximum of 5 stars


## Other Considerations

- TailwindCSS is preinstalled with the default config. It might be helpful for you, if you want to have some styles. (Not obligatory)

>
> 😀 The movie list is provided as boilerplate, but feel free to add your favorite one into the list.
>

>
> 👀 Don't peek at the solution until you've solved the exercise yourself or exhausted your resources. Challenging yourself will best prepare you for the exam
>


## Example of Finished App

This is an example of what the functionality should look like for the completed exercise. If you’d like to mimic this style, feel free to do so, but it is not required.

![Finished app in this challenge](https://images.certificates.dev/HV3dXET.png)

## Project Structure

```text
.
├── index.html              # HTML shell that loads the Vue application
├── src/
│   ├── main.js             # Creates and mounts the Vue app; imports global CSS
│   ├── App.vue             # Movie list UI and rating interactions
│   └── movies.json         # Static movie data
├── style.css               # Tailwind CSS directives
├── vite.config.mjs         # Vite configuration, Vue plugin, and @ alias
├── tailwind.config.js      # Tailwind content paths and typography plugin
├── postcss.config.js       # PostCSS configuration
├── eslint.config.js        # ESLint configuration
├── package.json            # Dependencies and development/build/lint scripts
├── public/                 # Static assets, including the favicon
├── images/                 # Challenge reference image
└── CHECKLIST.md            # Project checklist
```

The app starts from `index.html`, which loads `src/main.js`. That entry point mounts `App.vue`, where movie data from `movies.json` is made reactive, displayed as cards, and updated when a user selects a rating. Styling uses Tailwind utility classes, enabled through the directives in `style.css`.

This is a compact frontend with no router or backend/API layer. Movie ratings are held in memory and reset when the page reloads, while movie images are fetched from external URLs. If the app grows, the UI and data/state logic could be split into reusable components and modules.

## License

This project is licensed under the [MIT License](LICENSE).
