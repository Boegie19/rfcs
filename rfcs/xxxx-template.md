- Start Date: (2024-01-16)
- RFC PR:

# Summary
Implement a category dropdown in the admin UI for both Collection & Single types.

# Motivation
The motivation behind this proposal is to simplify content organization and improve the user experience while managing content in the Strapi admin interface. Currently, users have to navigate through a long list of Collection and Single types, which can be time-consuming and cumbersome, especially when dealing with numerous content types. By introducing a category dropdown, users can easily group and filter their content types, making content management more efficient and user-friendly.

# Detailed design
The proposed solution includes the following design changes:

1. Add a category dropdown in the admin UI for both Collection & Single types, enabling users to filter content types based on the selected category.
2. Allow users to create, edit, and delete categories from the Content Type Builder
3. un assign are loaded in between the categories in alphabetical order
4. The categories will have a displayName and no translation options like SingleTyps and Content-Types
5. If notting in the category is visible make the category invisible. 

Edge Cases:

- Handling empty categories: 
  1. If all content types within a category are deleted or moved to another category, the empty category should still be displayed in the dropdown to allow users to assign new content types to it.
  2. If a category is empty delete the category (This will be automatic since it is created in content-type files)
- Handling category deletion: If a category is deleted, all associated content types should be moved to the default category.

# Example
No changes to the current API are required for this proposal. The proposed changes are only related to the admin UI.

# Tradeoffs
Some tradeoffs to consider when implementing this proposal:

- Complexity: The addition of categories adds a new layer of complexity to the admin UI. However, the benefits of improved content organization and user experience outweigh this tradeoff.
- Workload of implementation: The implementation of this feature requires updates to the admin UI and possibly some backend changes. This might increase the workload for the Strapi team.
- Integration with current features: This proposal should not conflict with existing features and can be seamlessly integrated into the current admin UI.

The proposal does not require significant migration efforts, nor does it introduce breaking changes to existing Strapi applications. However, it might require updates to existing teaching resources, including videos, tutorials, and documentation to reflect the new category feature.

# Alternatives
- Do everyting in the database (This would mean that if you change the empty database you will lose all your categories)
- Have inital sturcture in Filesystem and allow the user to customize it this will be saved in the db. (This would be the option I want in the long term)

# Unresolved questions
- Should we allow multiple levels of categories inside of each other like the folders in media libary. (This should maby be implemented as a secondary step to this PR)
- What will be the maximum number of categories allowed (per level)? Is there a need for a limit?
- Will we allow drag and drop reodering of categories? (This should maby be implemented as a secondary step to this PR)