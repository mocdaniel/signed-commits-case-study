# Signed Commits - a case study

Signing commits drastically hardens your repository against attempts to commit malicious code, e.g. via commit spoofing. Commit signing in addition to some features of GitHub, such as [Vigilant mode](https://docs.github.com/en/authentication/managing-commit-signature-verification/displaying-verification-statuses-for-all-of-your-commits), can help you make sure to only accept verified commits by contributors you know and trust. 

This repository attempts to serve as a demo of the "look 'n feel" of commit signing on GitHub, and the different possibilities to do so.

We will look at three ways to sign commits - using `GPG` keys, `SSH` keys, and `gitsign` - and what the results look like on GitHub.

## Using GPG keys

### 1. Commit - signed by a valid user

The first commit is an authentic one:

- it was drafted by the **repository's owner** (`mocdaniel`) from his **verified email address** (`dbodky@gmail.com`)
- it has been signed by a GPG key which has been **linked** to the author's account.

You can have a look at the **commit history** of a repository at all times by navigating to the `Commits` tab in the top of the repo, or [following this link](https://github.com/mocdaniel/signed-commits-case-study/commits/main).

### 2. Commit - signed with a non-verified GPG key

The second commit is a bit weird:

- it seems to originate from `mocdaniel`
- **but** the GPG key is `unverified`?

Maybe the user just messed up his key management, or he forgot to **upload his public gpg signing key** for this key. Maybe it's a quite intricate attempt of getting malicious code in - in general it's better do decline commits like this or have a proper second look!

You can do so by cloning the repository and looking at the history via `git log --show-signature`, btw:

```console
git log --show-signature
commit 1bc84ab1f6b65e55e9dfec883fbe65c494d689d5 (HEAD -> main)
gpg: Signature made Wed 19 Jul 2023 06:07:01 PM CEST
gpg:                using EDDSA key 5530A1A2EF240BCE0AE9185EF478C71B38B9AD9E
gpg: Good signature from "Daniel Bodky <daniel.bodky@netways.de>" [ultimate]
Author: Daniel Bodky <dbodky@gmail.com>
Date:   Wed Jul 19 18:07:01 2023 +0200

    Second commit

commit 60b9d6a151cd08a21f134bb941cb4dbfc9cf395a
gpg: Signature made Wed 19 Jul 2023 06:05:13 PM CEST
gpg:                using EDDSA key 738DC9BC3F567CB282E5B29C9E12D1B1F1A84FA8
gpg: Good signature from "Daniel Bodky <dbodky@gmail.com>" [ultimate]
Author: Daniel Bodky <dbodky@gmail.com>
Date:   Wed Jul 19 18:05:13 2023 +0200

    First commit
```
### 3. Commit - Who's cloudnativeclutter?!

The third commit is *definitely* weird:

- it shows **cloudnativeclutter** (my blog's GitHub user) as author
- again, the commit is `unverified`, this time because I got **vigilant mode** configured for this account

Spoofing commits is as easy as changing the `user.email` and `author.email` field of your git config, thus changing the email address **GitHub** sees upon committing. Since GitHub is a **collaborative coding platform**, it will try to resolve this email address and display the author's information - totally fooling everyone who doesn't look twice!


## Using SSH keys

### 4. Commit - signed with a verified SSH key

The fourth commit is very similar to the first one:

- it comes from the repository's owner
- it is `verified`

The only difference is a tiny detail: Instead of a **GPG Key ID** we see a **SSH Key Fingerprint** when clicking on the `verified` badge now.
