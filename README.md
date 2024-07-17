# Test 4

Instructions for Local Actions using: https://nektosact.com/

For a test action see: https://github.com/smashedr/js-test-action

## Setup

1. Deploy your local action to `.github/your-action`
1. Edit [test.yaml](.github%2Fworkflows%2Ftest.yaml) to point to your local action using this
   format: `./.github/js-test-action`

You can now run your compiled action with `act`. Use `-l` to list and `-j` to specify if necessary.

To run your action from source with `node` you need to add the `node_modules` to the top leve directory:

1. Copy or install your node modules in the top level directory: `./node_modules`
1. Update your action's `action.yml` main to your source, example: `src/index.js`

You should now be able to make source changes, and run directly with `act`

## Notes

Make sure you do NOT have `node_modules` or `.github/**` in this `.gitignore` or use the `--use-gitignore=false` option.

The `.env`, `.secrets` and `.vars` files are defaults and automatically sourced. To source `event.json` you need to run
act with `act -e event.json`

If you are deploying/syncing with a remote server, make sure to include the `.git` folder for repository variables.

For advanced using with things like secrets, variables and context see: https://nektosact.com/usage/index.html

You should also review the options from `act --help`

## Directory Structure

Example Directory Structure:

.  
├── .github  
│ ├── js-test-action  
│ │ └── https://github.com/smashedr/js-test-action  
│ └── workflows  
│ └── test.yaml  
├── node_modules  
│ └── (must include all modules to run js-test-action)  
├── .env  
├── .gitignore  
├── .secrets  
├── .vars  
├── package.json  
├── package-lock.json  
└── README.md  
