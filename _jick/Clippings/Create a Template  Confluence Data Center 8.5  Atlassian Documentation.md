---
title: "Create a Template | Confluence Data Center 8.5 | Atlassian Documentation"
source: "https://confluence.atlassian.com/conf85/create-a-template-1283359868.html"
author:
published:
created: 2025-03-27
description:
tags:
  - "clippings"
  - "youtube"
---
#### Page Templates

- [Create a Template](https://confluence.atlassian.com/conf85/create-a-template-1283359868.html)
- [Create a Page from a Template](https://confluence.atlassian.com/conf85/create-a-page-from-a-template-1283359887.html)

#### On this page

- [Add a template](https://confluence.atlassian.com/conf85/#CreateaTemplate-Addatemplate)
- [The template editor](https://confluence.atlassian.com/conf85/#CreateaTemplate-Thetemplateeditor)
- [Template variables](https://confluence.atlassian.com/conf85/#CreateaTemplate-Templatevariables)
- [Labels](https://confluence.atlassian.com/conf85/#CreateaTemplate-Labels)
- [Images and other attachments](https://confluence.atlassian.com/conf85/#CreateaTemplate-Imagesandotherattachments)
- [Instructional text](https://confluence.atlassian.com/conf85/#CreateaTemplate-Instructionaltext)
- [Add a description to your template](https://confluence.atlassian.com/conf85/#CreateaTemplate-Addadescriptiontoyourtemplate)
- [Edit or delete a template](https://confluence.atlassian.com/conf85/#CreateaTemplate-Editordeleteatemplate)
- [Notes](https://confluence.atlassian.com/conf85/#CreateaTemplate-Notes)

#### Still need help?

The Atlassian Community is here for you.

[Ask the community](https://community.atlassian.com/t5/custom/page/page-id/create-post-step-1?add-tags=Confluence)

In Confluence, there are four categories of page templates:
- **Space templates:** These page templates are available in a specific space only. If you have [space administrator permission](https://confluence.atlassian.com/conf85/space-permissions-overview-1283359541.html), you can define templates via the space administration screen.
- **Global page templates:** These page templates are available in every space on your site. If you have [Confluence Administrator permission](https://confluence.atlassian.com/conf85/global-permissions-overview-1283360854.html), you can define global templates via the Confluence Administration Console.
- **Blueprints:** A [blueprint](https://confluence.atlassian.com/conf85/blueprints-1283359895.html) is a page template with added functionality to help you create, manage and organize content in Confluence, and there's a collection of predefined ones that ship with Confluence. You can also download additional blueprints from the [Atlassian Marketplace](https://marketplace.atlassian.com/search?application=confluence&q=template). You can customize the blueprint templates to suit your individual needs, disable particular blueprints or even develop your own blueprints.
- **System templates:** Confluence also provides 'system templates' containing content like the site welcome message and default space content. See [Administering Site Templates](https://confluence.atlassian.com/conf85/administering-site-templates-1283360927.html). If you edit a system template, it is referred to as a custom or edited system template.

## Add a template

**To create a new space template:**

1. Go to the space and select **Space tools** \> **Content Tools** from the bottom of the sidebar
2. Choose **Templates** \> **Create new template**.

**To create a new global template:**

1. Go to **Administration** > **General Configuration** **Global Templates and Blueprints**.
2. Choose **Add New Global Template**

**Looking for new Confluence templates?** A huge range of templates are now available in Confluence Cloud. Learn more about [templates in Confluence Cloud](https://www.atlassian.com/software/confluence/templates).

These templates are not available for Confluence Server or Data Center.

  

## The template editor

When you create or edit a template, you'll be [using the editor](https://confluence.atlassian.com/x/QQz2Dg) in much the same way as when you edit a page or blog post. In addition you can add variables, which will produce a form for data collection when anyone adds a page based on the template.

*Screenshot: The template editor with an image, table, text, and variables*

*![](https://confluence.atlassian.com/conf85/files/1283359868/1283359878/1/1692746749953/template+editor.png)  
*

*Screenshot: The form displayed when you create a page based on the template*

*![](https://confluence.atlassian.com/conf85/files/1283359868/1283359879/1/1692746750042/page+from+template.png)  
*

### Template variables

When you add variables to your template, they will act as form fields. When you create a page based on a template, you'll see a text entry box for each field. Enter data into each field, and it'll be added to the page.

You can add the same variable more than once in the same template, which is useful if you need the same information in more than one place on the page.

**To insert a variable into a template:**

1. Create a new template or **Edit** a template.
2. From the editor toolbar, select then choose **New Variable** (or choose an existing variable to add it to the page).
3. Enter a name for the variable.
4. Press **Enter** (by default this will create a single-line text input field).

To change the variable type, click the variable placeholder and the variable's property panel will appear. Choose one of the variable types: **Text**,  **Multi-line Text**, or  **List**.

You can change the number of lines and width in characters of a **Multi-line Text**  field. If you choose  **List**, enter each of the items in your list, separated by commas.

![](https://confluence.atlassian.com/conf85/files/1283359868/1283359880/1/1692746750111/multilinetext.png)

![](https://confluence.atlassian.com/conf85/files/1283359868/1283359881/1/1692746750175/list.png)

**Hint:** Type **$** and the variable name, then press **Enter** to add a new variable or to select an existing variable from a list of suggestions. The suggestions dialog shows variables already defined in this template.

If you'd like all pages created using this template to have one or more labels, choosethe labels icon next to the breadcrumbs at the top of the page to add them.

Note: Currently, it's not possible to edit the labels of blueprint templates.

### Images and other attachments

You can't upload an image or other file into a template directly. First you'll need to upload the file to a page in your site, then in your template, choose **Insert** > **Files** \> **Search on other pages** to embed the file or image.

### Instructional text

Instructional text is placeholder content in a template, and is only visible while you're editing the page. Use it to give guidance to whoever is creating a page from the template.

**To insert instructional text:**

1. Create a new template or **Edit** a template.
2. From the editor toolbar, select then choose **Instructional text.**
3. Type in your instructional text (for example, *Insert an image of the interface here.*)

Instructional text appears in italics with a shaded background, to distinguish it from normal paragraph text.

You can also change the placeholder type from **Text** to either:

- **User mention** – Opens the user mention dialog.
- **Jira Macro** – Opens a dialog that allows you to create a new Jira issue, or search for one or more Jira issues to include on the page.

## Add a description to your template

The template description displays in the 'Create' dialog, and is useful for explaining the purpose of your template to other users.

**To add a description to a template:**

- Go to the space or global templates page (as described above )
- Choose the **Edit** icon in the 'Description' column
- Enter your description and choose **Save**

**![](https://confluence.atlassian.com/conf85/files/1283359868/1283359877/1/1692746749885/template-description.png)**

1. **Edit**: use the pencil icon to edit your template's description.

## Edit or delete a template

If you need to change anything about your template, or want to delete it, navigate to either your space or global template (as described [above](https://confluence.atlassian.com/conf85/#CreateaTemplate-above) ) and choose either  **Edit** or  **Delete**.

## Notes

- Page templates are used only when adding a page. It is not possible to apply a template to an already-existing page. Once a page has been added using a template, the template is no longer linked to the page. All further editing is performed as if the template was never used. Some Marketplace apps provide enhanced template functionality. You can search the [Atlassian Marketplace](https://marketplace.atlassian.com/search?application=confluence&q=template) for template apps.
- When you use a [Table of Contents macro](https://confluence.atlassian.com/conf85/table-of-contents-macro-1283360361.html) in a template, you'll see an error when you preview the template, but the Table of Contents macro works on the pages that people create from the template.
- The editor for templates is available only in **Confluence 4.3 and later**. Please refer to the [earlier documentation](https://confluence.atlassian.com/display/CONF42/Adding+a+Template) for a description of the wiki markup editor templates.
- Confluence also provides 'system templates' containing content like the site welcome message and default space content. See [Administering Site Templates](https://confluence.atlassian.com/conf85/administering-site-templates-1283360927.html).

Last modified on Aug 22, 2023

Was this helpful?

Yes No Provide feedback about this article Powered by [Confluence](http://www.atlassian.com/) and [Scroll Viewport](https://www.k15t.com/go/scroll-viewport).