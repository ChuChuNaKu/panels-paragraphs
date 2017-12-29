This page is intended to outline a few of the strengths and weaknesses of using **[Panels](https://www.drupal.org/project/panels)** and **[Paragraphs](https://www.drupal.org/project/paragraphs)** as content architecture solutions.
___


# Paragraphs

### Pros:

**Content Editing Experience**
* Gives content editors great flexibility in managing content by allowing them to select which kinds of Paragraphs they want to place on the page.
* Paragraphs is especially useful on sites with row based layouts.
* Paragraphs can serve as a great alternative to Field Collections when you need to repeat field values within a parent entity.
* Content editors with some Drupal experience should feel comfortable using Paragraphs because it uses Drupal's Entity API system and is fieldable.

**Translation**
* The Paragraphs module works within a multilanguage setup but with a few constraints.

**Revisions**
* Entity Reference Revisions is the only module requirement and it allows Paragraphs to become revisioned along with the node they are attached to.

**Editorial Workflows**
* Paragraphs supports Content Moderation workflows. For example, when you change paragraphs content on a new draft, the changes stay in draft and are not immediately visible to anonymous users.

**Search**
* Drupal's default search is capable of indexing Paragraph entities as part of their parent nodes.
* The paragraphs_demo module that is included with Paragraphs contains an example search index that indexes paragraphs.

**Reusable Entities**
* Paragraph Types can be reused in different reference fields.

**Lightning Distribution Compatibility**
* Paragraphs is compatible with the [Lightning distribution](https://www.drupal.org/project/lightning)

**Acquia Lift Compatibility**
* Paragraphs is compatible with Acquia Lift 3.

**Acquia Content Hub Compatibility**
* As of [version 8.x-1.7](https://docs.acquia.com/release-note/content-hub-8x-17) Content Hub  [supports the Paragraphs module in Drupal 8](https://docs.acquia.com/content-hub/modules) for import and export in a node. Paragraphs that are set to use local changes will support cascading those changes to both ancestor and dependent entities.

**Module Stability**
* The [Paragraphs](https://www.drupal.org/project/paragraphs) and [Entity Reference Revisions](https://www.drupal.org/project/entity_reference_revisions) modules have stable Drupal 8 releases.

**Theming**
* Paragraphs returns render elements and provides template suggestions for bundles and view modes.

**Migration**
* Migrations are supported with Paragraphs.

### Cons/gotchas

**Content Editing Experience**
* Content editors won't know how content will appear until after the Paragraph is saved. Paragraphs works with quick edit, but it sees the field as a whole, meaning using quick edit will show the full paragraphs field in the popup. A proposed resolution includes [extending the quickedit functionality](https://www.drupal.org/node/2476863).
* Editing experience can get unwieldy if there are multiple Paragraph types on the entity edit screen

**Translation**
* The fields on the paragraphs item entity are translatable, but the [paragraph field on the parent entity are not](https://www.drupal.org/node/2735121).
* If you have a translatable node with a paragraph, [deleting one of the translations causes the content of the node to be deleted](https://www.drupal.org/project/paragraphs/issues/2832592).
* Paragraphs does not support [translatable paragraph entity reference revision fields](https://www.drupal.org/project/paragraphs/issues/2461695).

**Reusable Entities**
* It's possible to reuse paragraph types but not [paragraph entities](https://www.drupal.org/project/paragraphs/issues/2414865).

**Revisions**
* Reverting revision doesn't work on paragraphs if a [parent node has translations](https://www.drupal.org/project/paragraphs/issues/2924168)

**Migration**
* [Paragraphs is not yet supported in the automated upgrade included in Drupal core](https://www.drupal.org/project/paragraphs/issues/2841593).   

# Panels
### Pros:
**Content Editing Experience**
* Panelizer and PageManager are two modules that implement panels. PageManager creates pages or routes that have layouts and Panelizer embeds blocks into entities. Panelizer also acts as a display mode that overrides an entity's default display mode.
* Panels provides a WYSIWYG layout and editing experience with IPE (In Place Editor) giving content editors an easy way to arrange and place content.
* A few of the ideas behind Panelizer and Page Manager are [making their way into Drupal Core](https://www.drupal.org/project/panels/issues/2820125).
* The Layout Discovery module was included in Drupal 8.3 and adds [a Layout API to core](https://www.drupal.org/docs/8/api/layout-api). Both Panelizer and Panels adopted the new Layout API with their 8.4 release.
* The [field layout module was added to Drupal core](https://www.drupal.org/project/drupal/issues/2796173) in 8.3. and adds layout integration to the field ui allowing you to apply layouts to content types.

**Lightning Distribution Compatibility**
* Panels, PageManager, and Panelizer are included in [the Lightning distribution](https://docs.acquia.com/lightning/modules)

**Module Stability**
* [Panels](https://www.drupal.org/project/panels) and [Panelizer](https://www.drupal.org/project/panelizer) have stable releases

**Separation of Concerns**
* Panels layout and display are managed separately from data. For example, blocks are created in Drupal and then placed with Panelizer and PageManager.


### Cons:
**Translation**
* [Multilingual support for Panelizer](https://www.drupal.org/project/panelizer/issues/2778565) is being worked on. The [patch attached to this issue](https://www.drupal.org/project/panels/issues/2793801) is needed for Panelizer on multilingual sites. Otherwise, temporary changes made on one language of an entity are shown on all languages without overrides.

**Content Editing Experience**
* The content editing experience may confuse content editors when some content is editable with IPE and other content requires using the node edit form.
* IPE only appears when a [node is in a draft state](https://www.drupal.org/project/lightning/issues/2854054). This can lead to some confusion unless you explicitly know to do this.

**Editorial Workflows**
* Panelizer has no explicit code [to support Workbench/Content Moderation or the concept of forward revisions](https://www.drupal.org/project/panelizer/issues/2925942).
* A ticket was created to explore ways to [improve how Panelizer defaults are handled](https://www.drupal.org/project/panelizer/issues/2704859). For example, novice users may not be fully aware of what saving a default really does.

**Migration**
* [Migrate support doesn't exist yet for Panelizer](https://www.drupal.org/project/panelizer/issues/2860513)

**Revisions**
* IPE is unable to [update revisions of pinned content blocks](https://www.drupal.org/node/2844054)
