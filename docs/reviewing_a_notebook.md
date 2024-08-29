# Reviewing a Notebook

This guide will walk you through the process of reviewing Jupyter notebooks using GitNotebooks. We'll cover how to add comments, understand diffs, and submit reviews.

## Viewing a Notebook Change

When you open a new pull request that includes changes to Jupyter notebooks, GitNotebooks automatically adds a comment to your pull request. This comment contains a link inviting you to review the notebooks using GitNotebooks.

<img src="./images/review/review-notebook-link.png" alt="Start a review image" width="700" />

## Adding and Viewing Comments

Once you have opened up a review in GitNotebooks, you can add comments to both code and markdown cells.

### Code Comments

You can add single-line or multi-line comments on either the left or right side of the code.

<div style="display: flex; justify-content: space-between;">
  <div style="width: 48%;">
    <h4>Single-line Comment</h4>
    <img src="./images/review/code-comment.png" alt="Image showing single-line code comment" width="100%">
  </div>
  <div style="width: 48%;">
    <h4>Multi-line Comment</h4>
    <img src="./images/review/mulit-line-code-comment.png" alt="Image showing multi-line code comment" width="100%">
  </div>
</div>

### Markdown Comments

To comment on markdown, simply click directly on the markdown text. Each markdown comment is associated with a specific line in the markdown, ensuring your feedback is always in context.

When a comment is added to markdown, a blue underline will appear. To view the comment and respond, click the markdown or the avatar to the right.

You can view markdown diffs in both rendered and raw formats, giving you the option to review the content in the way that works best for you. To learn more see our [settings docs](./settings.md)

<div style="display: flex; justify-content: space-between;">
  <div style="width: 48%;">
    <h4>Adding a markdown comment</h4>
    <img src="./images/review/add-markdown-comment.png" alt="Image demonstrating how to add comments to markdown cells" width="100%">
  </div>
  <div style="width: 48%;">
    <h4>Replying to a markdown comment</h4>
    <img src="./images/review/view-markdown-comment.png" alt="Image demonstrating viewing a markdown comment" width="100%">
  </div>
</div>

### Notes About Comments

Comments will stay in place as new commits are pushed to the branch.

Comments are automatically marked as outdated if a new commit changes the specific line since the comment was added.

<img src="./images/review/outdated.png" alt="Image showing an outdated review comment" width="700">

## Viewing Diffs

GitNotebooks supports a variety of diffs to make your review process comprehensive:

- Rendered and raw markdown diffs
- Code diffs
- Dataframe output diffs
- Text output diffs
- Chart and image change detection

### Code Diffs

Code diffs are rendered similarly to GitHub.

Context around the changed line is collapsed. Click the blue line to expand the diff context.

<img src="./images/review/diff-context.png" alt="Image showing the code diff in a notebook with the ability to expand above and below" width="700">

### Markdown Diffs

Markdown diffs are presented in both rendered and raw formats, allowing you to see both the visual changes and the underlying markup modifications.

<div style="display: flex; justify-content: space-between;">
  <div style="width: 48%;">
    <h4>Rendered Markdown Diff</h4>
    <img src="./images/review/rendered-markdown-diff.png" alt="Image showing rendered markdown diff in a notebook" width="100%">
  </div>
  <div style="width: 48%;">
    <h4>Raw Markdown Diff</h4>
    <img src="./images/review/raw-markdown-diff.png" alt="Image showing raw markdown diff in a notebook" width="100%">
  </div>
</div>

### Output Diffs

Output diffs are useful when reviewing changes in notebook results. This includes changes in dataframes, text outputs, charts, and images.

<div style="display: flex; justify-content: space-between;">
  <div style="width: 32%;">
    <p style="font-size: 0.9em;">Dataframe Diff</p>
    <img src="./images/review/dataframe-diffs.png" alt="Image showing the diff of a dataframe" width="100%">
  </div>
  <div style="width: 32%;">
    <p style="font-size: 0.9em;">Text Output Diff</p>
    <img src="./images/review/raw-output-diff.png" alt="Image showing the diff of text" width="100%">
  </div>
  <div style="width: 32%;">
    <p style="font-size: 0.9em;">Chart Diff</p>
    <img src="./images/review/chart-diff.png" alt="Image showing the diff of a chart" width="100%">
  </div>
</div>

## Submitting a Pull Request Review

To submit your review in GitNotebooks:

1. Click the "Start a review" button on any comment you make.
2. Add comments throughout the notebook as needed.
3. When ready to submit your review, click "Finish your review".
4. Choose to approve, reject, or leave a neutral review, similar to GitHub's review process.

After submitting your review, all your comments will be posted to GitHub automatically.

<div style="display: flex; justify-content: space-between;">
  <div style="width: 48%;">
    <p>Step 1: Start a review</p>
    <img src="./images/review/review-first-comment.png" alt="Image showing how to start a review in GitNotebooks" width="100%" />
  </div>
  <div style="width: 48%;">
    <p>Step 2: Add comments</p>
    <img src="./images/review/review-add-comment.png" alt="Image showing how to add comments during a review in GitNotebooks" width="100%" />
  </div>
</div>
<div style="margin-top: 20px;">
  <p>Step 3: Submit the review</p>
  <img src="./images/review/review-submit.png" alt="Image showing how to submit a completed review in GitNotebooks" width="100%" />
</div>

## GitHub Synchronization

- Single comments and posted review comments appear in GitHub.
- Responses to comments made within GitHub are visible in GitNotebooks.
- Conversation threads can be resolved in GitNotebooks, which stays in sync with conversation resolution in GitHub.
