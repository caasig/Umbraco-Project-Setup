# Umbraco Project Setup

These are the base files and instructions on implementation needed for new Umbraco Projects. We recommend setting these up before branching to multiple environments with Git.

## Umbraco CMS

1. Install via Nuget.

	```
	PM> Install-Package UmbracoCms
	```
2. Add .gitignore file from this repository.

## uSync

uSync in an Umbraco package that takes the bits of Umbraco that are stored in a database and moves them to disk, so you can source control, copy, and move your Umbraco site between computers and servers. It will NOT sync content. It is free.

1. Install via Nuget.

	```
	PM> Install-Package uSync
	```

Note: A "uSync" directory will be created when installing the package via Nuget. It will contain XML config files for everything in your database. When new Document Types or Data Types are created from the Umbraco Backoffice, it will automatically generate the necessary config file. When a project builds, it will import everything from the uSync folder. For example, when merging from a Dev to Staging branch, the uSync folder will merge over and will be imported the next time the project builds on Staging. This will keep your database always in sync between environments.

## Courier

Courier compares and transfers your content, document types, templates, media, media types, macros, CSS, images, and scripts. It requires a one-time fee license (currently $139).

Since we are using uSync for syncing Document Types and Data Types between environments, Courier is not required. It is still recommended for the handling of content and media assets between environments and can be an incredibly useful tool for saving time.

1. Create new directory in root of project called "Umbraco_Packages".
2. Download Courier to new "Umbraco_Packages" directory. https://our.umbraco.org/projects/umbraco-pro/umbraco-courier/
3. Open Umbraco Backoffice and Developer Tab. Select Packages. Install Local and Upload Package.

Note: We recommend downloading packages manually and storing in Source Control to avoid conflicts in versioning between environments. If packages are added after setting up multiple environments, they will need to be installed in each environment's Backoffice.

4. Purchase Courier Express License. https://umbraco.com/products/umbraco-courier/
5. Follow instructions to register Local, Development, Staging, and Production URL's with License.
6. Once the License is received, add to "bin" directory.
7. Configure courier.config file from this repository on lines 6-22 for each environment registered with License. Add to "Config" directory when complete.




