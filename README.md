CNERG Documentation
====================

(Note: Sphinx versions higher than 1.1.2 are required.)

A 2 branch system has been implemented to maintain a clean process of
rebuilding this site.

1. The `source` branch contains the restructured text documents and
Sphinx configuration used to build the site.  All direct editing of
files should be made in the `source` branch.

2. The `master` branch contains the processed and published web
content that is derived by Sphinx from the `source` branch.  These
files should not be editted directly.

Best practice workflow for contributing to site changes
--------------------------------------------------------

1. Checkout the `source` branch

   ```git checkout source```

2. Synchronize your branch with the repository (either `pull` or
`fetch` and `merge`)

     ```git pull origin```

3. Create a branch to contain your change

     ```git checkout -b add_some_info```

4. Make your changes in this branch

5. Test you changes by using the `gh-preview` target

     ```make gh-preview```

   This will build a version of the site based on your branch,
   `add_some_info`.  You can load it directly in a local browser.

6. To revert to your source branch use the `gh-revert` target and then
   check out your branch.

     ```make gh-revert
     git checkout add_some_info```

7. Repeat steps 4-6 until satisfied.

8. Once satisfied with the source RST files, push your branch to the
repo.  Be sure to synchronize with any possible changes to the
`source` branch first.

     ```git fetch origin
     git rebase origin/source
     git push origin add_some_info```

9. Issue a pull request by going to your branch on the repo and
clicking the "Pull Request" button.

Best practice for managing a pull request
------------------------------------------

1. Synchronize your repository with the remote repo

     ```git fetch origin```

2. Checkout the `pull_request_branch`

     ```git checkout -b pull_request_branch```

3. Test you changes by using the `gh-preview` target

    ```make gh-preview```

   This will build a version of the site based on your branch,
   `pull_request_branch`.  You can load it directly in a local
   browser.

4. To revert to the `pull_request_branch` use the `gh-revert` target and then
   check out the branch.

     ```make gh-revert
     git checkout pull_request_branch```

5. If satisfied, merge the `pull_request_branch` into the `source`
branch.  Be sure to synchronize with the remote repo first.

     ```git checkout source
     git fetch origin
     git rebase origin/source
     git merge pull_request_branch```

6. If there are no conflicts, push this to the repo

     ```git push origin source```

7. Republish the pages with the `gh-pages` target.

     ```make gh-pages```

