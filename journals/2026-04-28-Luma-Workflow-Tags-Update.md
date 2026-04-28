# Luma Workflow Tags Update

Date: 2026-04-28
Agent: Luma
Task: Add Video Specific Tags to the Luma MainDB workflow
Timezone: Europe/Stockholm

## Source inputs
- Existing Ghost Master MainDB page and transcript review
- Luma MainDB packaging skill
- Luma task journal template

## Output produced

### Summary
- Updated the Luma packaging workflow so future runs generate 3 episode-specific YouTube tags and store them in the Video Specific Tags property.

### Deliverables
- Patched luma-main-db-video-pages to require and verify Video Specific Tags
- Patched luma-task-journal to record generated tags in the journal entry
- Updated journals/_luma_template.md to include a Video Specific Tags line in Deliverables

### Notes
- The Ghost Master page now contains three specific tags in the correct Notion property.
- The workflow now verifies that tags are present before the run is considered complete.

### 1-5 packaging scores
- Idea: 5
- Title: 5
- Thumbnail: 5
- Hook: 5
- Description: 5
- Overall package: 5

### Evaluation notes
- The new tags are specific to the episode instead of generic game metadata.
- The journal template now records the generated tags for future traceability.
- The workflow update preserves the existing page structure and only adds the missing property coverage.

### Overall package verdict
- Package

### Full output
Luma packaging workflow update completed. Future runs should now generate 3 highly specific video tags from the premise and transcript and write them to the Video Specific Tags property.

### Final takeaway
The Luma workflow now covers title, thumbnail, hook, description, and tags consistently.
