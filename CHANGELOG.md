# Improved `@` mention search
### [1.0.340] - 2025-08-15 (Fri. Aug 15)
We improved the way `@` mention search works
- Improved fuzziness of search
- Space bar allows you to continue searching, and searches across keywords, e.g. if you search `operation route` it'll pull up the `route.ts` file in the `operation` folder. This is useful for frameworks like NextJS where many files are called `page.tsx` or `route.tsx`
- We now show a nice file path view and the full relative path of the file so you're making
<img width="1766" height="920" alt="image" src="https://github.com/user-attachments/assets/32e5245b-c236-41fd-888e-7b4f942e96d6" />

# Improved git workflow for working with your Claude Code Sessions
### [1.0.339] - 2025-08-15 (Fri. Aug 15)
We felt the pain of working with Git Worktrees, and the strangeness of some of the workflows that came up when wanting to test. It felt off to have to test branches inside of the git worktrees, and most users don't care about the details of how git worktrees work. 

Now we hope the workflow feels more intiutive for you, and how you naturally work with `git` for the most part.

You don't need to test your changes inside the git worktree, when you want to test changes you either use the `Sync & Checkout Branch` button to test your changes locally in your actual repo branch (i.e. not inside the worktree that Claude Code ran in). When you open a PR or ask Claude to, it will be pushed to the right PR that is aligned with what the Sync & Checkout Branch does. 

<img width="583" height="46" alt="image" src="https://github.com/user-attachments/assets/7c95995b-2e44-40a1-9fa2-1427b8946dd7" />

Pressing sync & checkout just syncs changes out of the worktree into your actual branch, and just copies the check out command for the branch so you end up with something familiar in your clipboard like:
`git checkout magnet/change-toast-to-make-it-take-details` 

Our design goals were:
- Keep changes that Claude Code does inside of a sandbox (git worktree) so that it's isolated and parallelizable
- Make it easy for users to test changes the way they're used to: in the environment where they're already working
  - It felt like a bad UX to tell users to re-set up their app config in the worktrees and to start their application again in the worktree to test it. Our new approach makes it much faster to verify changes, because you just check out the branch where your server was already running, so no need to recompile, or run config scripts again, and things just hot reload where possible. This is a big deal when you want to quickly verify lots of changes.
- Make the PR match the branch name that gets synced. And make it so that you can still `gh pr checkout`

In an upcoming release, we'll also handle how the Claude Session stays up to date with any changes in your PRs or in your main environment.

# AI Issue Title Suggestion & Draft State for Issues
### [1.0.338] - 2025-08-13 (Wed. Aug 13)

- AI-Powered Issue Title Suggestions - Automatically suggest relevant issue titles based on your description. **Needs an Anthropic API key to be set in Settings**
  
![Issue Title Suggestions](https://github.com/user-attachments/assets/99f81511-826d-4374-9815-727dc6925d7c)

- Draft State Persistence for issues - Your issue drafts are now automatically saved so you never lose work in progress
- **Small fixes:**
  - Optimistic Deletion of Issues
  - Better Delete Confirmation dialog interactions - the delete button is what's focused so you can press Enter

# Improved Claude Code Chat UX & Quick Peek Sessions
### [1.0.337] - 2025-08-13 (Wed. Aug 13)

There's a ton of UX improvements in this branch, and lots more inbound!

- We made a big overhaul to the UX of the product trying to speed up how quickly you can get into Claude Code sessions
- You can open all the parallel Agent that are active from the Issues page in a side drawer for quick access
- Ability to stop Claude Code while it's responding
- Re-designed Suggested Context interaction. Get `@` mention suggestions based on your issue description.
- Revamped onboarding flow to make it faster to get into the app & shipping features!
  
![Open Sessions Quickly](https://github.com/user-attachments/assets/e4c74e09-c6af-4658-8a81-8a33e266301e)

<img width="1180" height="878" alt="image" src="https://github.com/user-attachments/assets/cdbad1bc-becb-4622-9449-d34fd0072d8c" />
