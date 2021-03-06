# gh-wiki-category-hook

This is a pre-commit hook for GitHub wikis (Gollum wikis).

Based on category sections you put in your pages, the hook generates and updates index pages for each category it finds.

It probably needs to be rewritten.

Let me know of any issues or questions.

# Usage

1. Clone your wiki's git repository.
2. Move, copy, or link "pre-commit" to .git/hooks/pre-commit in your repository.
3. Add "Categories" sections to your pages. Each should contain intra-wiki links to categories you want to define.
4. Commit your changes. Category pages are generated and/or updated.

# Limitations

## Local only

Since the hook only runs on your local machine, there's no way to enforce updates to the categories if you (or someone else) edits from the web-interface.

To mitigate this, you need to occasionally run the pre-commit hook yourself and push the changes.

If you're feeling particularly clever, you can set up GitHub to send wiki-edit events to a server to do this automatically, but that's not provided here. 

## Indexes are autogenerated only

Editing the category page indexes manually isn't supported. Any changes you make to a "Pages" section will be overwritten when the hook is run. However, you CAN edit the rest of the category page. For example, you can provide a description of the category and it will remain untouched.

## Stashes uncommitted changes

The hook tries to only work with your committed changes, so it runs "git stash". However, it doesn't run "git stash pop" afterwards. You have to do that yourself.

## Doesn't add new category pages

Category page changes are added with "git add -a", which only works on files alreadry tracked by git.

Until this is implemented better, you'll have to add each category page to git when it's first created. 
