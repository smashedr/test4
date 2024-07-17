# Test 4

Instructions for Local Actions using: https://nektosact.com/

For a test action see: https://github.com/smashedr/js-test-action

1. Deploy your local action to `.github/your-action`
1. Edit [test.yaml](.github%2Fworkflows%2Ftest.yaml) to point to your local action using this
   format: `./.github/js-test-action`

You can now run your compiled action with `act`. Use `-l` to list and `-j` to specify if necessary.

To run your action from source with `node` you need to add the `node_modules` to the top leve directory:

1. Copy or install your node modules in the top level directory: `./node_modules`
1. Make sure you do NOT have `node_modules` or `.github/**` in this `.gitignore`
1. Update your action's `action.yml` main to your source, example: `src/index.js`

You should now be able to make source changes, and run directly with `act`

For advanced using with things like secrets, variables and context see: https://nektosact.com/usage/index.html

Example Directory Structure:

.  
├── .github  
│ ├── js-test-action  
│ │   └── https://github.com/smashedr/js-test-action  
│ └── workflows  
│     └── test.yaml  
├── node_modules  
│   └── (must include all modules to run js-test-action)  
├── .gitignore  
├── package.json  
├── package-lock.json  
└── README.md  
