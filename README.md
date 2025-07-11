Overpowered Writing Tools
=========================
This repository provides a collection of tools to manage the writing repository described in An Overpowered Writing System (TODO LINK).

It expects a writing repo in the Overpowered Writing System format:

```
TEMPLATE/
    post.md
    images/
some-post/
    post.md
    images/
        image.png
some-other-post/
    post.md
    images/
        image.png
```

Installation
------------
1. Clone this repo:
   ```
   git clone git@github.com:mieubrisse/overpowered-writing-tools.git
   ```
1. Add the following to your `.bashrc`/`.zshrc`, replacing the `TODO`s with the appropriate values:
   ```
   export WRITING_REPO_DIRPATH=/TODO/your/writing/repo/path
   source /TODO/clone/location/of/overpowered-writing-tools/sourceme.sh
   ```
1. (Optional) set up aliases as you please:
   ```
   alias pf="find_post"
   alias pn="new_post"
   ```

Usage
-----
The `sourceme.sh` file makes two functions available, which you may consider aliasing:

### find_post
`find_post [search_term] [search_term2]..` will:

1. Collect all post directories across all branches in `$WRITING_REPO_DIRPATH`
1. Present the user with a list, which is interactively filterable using [`fzf`](https://github.com/junegunn/fzf)
1. Upon selection, switch to the post's branch and open the `post.md` in the user's `$EDITOR`

### new_post
`new_post post_word1 [post_word2]...` will:

1. Create a new branch on `$WRITING_REPO_DIRPATH` by joining the post word args with `-` (e.g. `new_post my new post` creates `my-new-post`)
1. Clone the `TEMPLATE` directory to create a new directory with the same name as the branch
1. Open `post.md` in the user's `$EDITOR`
