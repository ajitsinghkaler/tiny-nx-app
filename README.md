# What is done with the app

We have generated an Nx workspace with a single Angular application. Even before adding any features, we can extract workspace libraries to adhere to the Single Responsibility Principle.

## The assets library

The shared assets workspace library contains static files such as web fonts, icons, and images. It also contains the favicon. The web app manifest would also be added here.

We saw an example of adding an image file to this library and referring to it from our application project. Of course, this works from UI workspace libraries and feature libraries as well.

With static files located in a separate workspace library, we lower the risk of breaking the whole application when adding, deleting or modifying static files.

## The styles library

With a workspace library exclusively for global styles, we won't have to feel bad for polluting the application project with dozens of Sass partials or risk breaking the application setup by accident.

The shared styles workspace library could also expose Sass mixins, functions, and partials that are shared between component styles or UI workspace libraries.

## The environments library

Extracting the environment files to a shared workspace library allows us to conditionally configure injectors from workspace libraries such as the shared data access library we created to configure NgRx Store in the root injector.

In a real application, we could add a feature shell library so that it would become the orchestration Angular module imported by AppModule or CoreModule.

Without a feature shell library, we have to make changes to the application project to add further configure the root injector or add application use cases. This is risky. We're better off leaving the application project untouched under most circumstances to have peace of mind.

## Shared workspace libraries

In the examples demonstrated in this article, we have put the extracted workspaces libraries in the shared library grouping folder and added the scope:shared tag. For workspaces with only a single application, this might not be necessary.

However, as the application grows, we will be happy that we used grouping folders from the beginning of the project. Application-wide workspace libraries are in the shared grouping folder, while we use for example sub-domain grouping folders to group our feature libraries and their related data access, domain, and UI workspace libraries.

Alternatively, we would end up with dozens if not hundreds of library folders within the libs folder, each with increasingly long folder names.

If it turned out that we wanted to add additional applications to the workspace, we would keep the workspace libraries that we wanted to share between the applications in the shared library grouping folder. The ones that we could or would not want to share between the applications could be placed within a library grouping folder named after the application, for example libs/tiny-app/shared for application-wide libraries unique to the tiny-app application project.
