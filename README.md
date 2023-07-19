# Signed Commits - a case study

Signing commits drastically hardens your repository against attempts to commit malicious code, e.g. via commit spoofing. Commit signing in addition to some features of GitHub, such as [Vigilante mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits), can help you make sure to only accept verified commits by contributors you know and trust. 

This repository attempts to serve as a demo of the "look 'n feel" of commit signing on GitHub, and the different possibilities to do so.

We will look at three ways to sign commits - using `GPG` keys, `SSH` keys, and `gitsign` - and what the results look like on GitHub.

## Using GPG keys

### 1. Commit - signed by a valid user

The first commit is an authentic one:

- it was drafted by the **repository's owner** (`mocdaniel`) from his **verified email address** (`dbodky@gmail.com`)
- it has been signed by a GPG key which has been **linked** to the author's account.

You can have a look at the **commit history** of a repository at all times by navigating to the `Commits` tab in the top of the repo, or [following this link](https://github.com/mocdaniel/signed-commits-case-study/commits/main).

