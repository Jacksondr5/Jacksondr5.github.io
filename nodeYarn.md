#### Installing Node and Yarn

In order to run any of the software I've described on this site, you'll need to download Node and Yarn, as well as configure them to work on our corporate network. I've described what Node is in [another part of the site](https://jacksondr5.github.io/nodeExpress). [Yarn](https://yarnpkg.com/en/) is a package manager built off of Node's npm. It accesses the [largest open source repository in the world](https://www.npmjs.com/) to manage your dependencies. Using Yarn actually makes it very easy to manage dependencies. All dependencies are local to your project, so you don't have to worry about conflicting with other apps running on the same box. Yarn also creates and references the `package.json` file, which keeps a list of all the dependencies in the project. This way, we can pass the app's code around without needing to pass the dependencies around too. All someone needs to do to set up a project is get the source code and run `yarn` in the command line.

Some important things to note:

* npm and Yarn can be used interchangibly. Wherever you see `npm install` you can just type `yarn add`. I recommend Yarn over npm because it caches dependencies and also flattens the dependency tree. NEAT uses Yarn, running `npm install` can potentially mess up the nice flat dependency tree I've got going. Please don't do that.

## Installation Instructions

1. Download Node [here](https://nodejs.org/en/). Node will come with npm, which you need to make Yarn work. Be sure to install the latest LTS version (8 as of writing), not the current version (9 as of writing). Run the installer.
2. Download Yarn [here](https://yarnpkg.com/en/docs/install). Run the installer.
3. Configure npm to work behind our corporate proxy. npm relies on a SSL certificate chain to work, and it doesn't like the self-signed AgF certificate unless you tell it to. If you already have an AgF certificate, you can skip to step 6.
4. Follow [these instructions](https://docs.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in) until step 6. After adding the snap-in navigate to Console Root -> Certificates -> Trusted Root Certificate Authorities -> AgFirst Farm Credit Bank.
5. Open the certificate, and under **Details** select **Copy to File...**. Export the certificate **as a .CER** to a good place.
6. Go back to cmd/PowerShell and type `npm config set cafile C:\\path\to\your\cert.cer`

You should now be set up to use Node and Yarn. Continue on to learn how to set up a [React app](https://jacksondr5.github.io/setupReactApp) or a [GraphQL server](https://jacksondr5.github.io/setupGraphqlServer).
