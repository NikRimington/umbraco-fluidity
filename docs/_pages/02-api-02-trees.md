---
layout: default
section: API
title: Trees
permalink: /api/trees/index.html
---

A tree is a hierarchical structure to help organise a section into logical sub-sections and is accessed in the main side panel of the Umbraco interface. In Fluidity, a section may only have a single tree definition, however you can use folder nodes to help organise the tree structure how you need it.

### Defining a tree

You define a tree for a section by calling the `SetTree` method on the given [`FluiditySectionConfig`]({{ site.baseurl }}/api/sections/) instance.

#### SetTree(string name, Lambda treeConfig = null) *: FluidityTreeConfig*
{: .signature}

Sets the tree with the given name to display in the Umbraco side panel for the given section.

````csharp
// Example
sectionConfig.SetTree("Database", treeConfig => {
    ...
});
````

### Changing a tree alias
{: .mt}

#### SetAlias(string alias) *: FluidityTreeConfig*
{: .signature}

Sets the alias of the tree.  

**Optional:** When creating a new tree, an alias is automatically generated from the supplied name for you, however you can use the `SetAlias` method to override this should you need a specific alias.

````csharp
// Example
treeConfig.SetAlias("database");
````

### Adding a folder to a tree
{: .mt}

#### AddFolder(string name, Lambda folderConfig = null) *: FluidityFolderConfig*
{: .signature}

Adds a folder to the current tree with the given name and a default folder icon. See the [Folders API documentation]({{ site.baseurl }}/api/folders/) for more info.

````csharp
// Example
treeConfig.AddFolder("Settings", folderConfig => {
    ...
});
````

---

#### AddFolder(string name, string icon, Lambda folderConfig = null) *: FluidityFolderConfig*
{: .signature}

Adds a folder to the current tree with the given name + icon. See the [Folders API documentation]({{ site.baseurl }}/api/folders/) for more info.

````csharp
// Example
treeConfig.AddFolder("Settings", "icon-settings", folderConfig => {
    ...
});
````

### Adding a collection to a tree
{: .mt}

#### AddCollection&lt;TEntityType&gt;(Lambda idFieldExpression, string nameSingular, string namePlural, string description, Lambda collectionConfig = null) *: FluidityCollectionConfig&lt;TEntityType&gt;*
{: .signature}

Adds a collection to the current tree with the given names and description and default icons. An ID property accessor expression is required so that Fluidity knows which property is the ID property. See the [Collections API documentation]({{ site.baseurl }}/api/collections/) for more info.

````csharp
// Example
treeConfig.AddCollection<Person>(p => p.Id, "Person", "People", "A collection of people", collectionConfig => {
    ...
});
````

---

#### AddCollection&lt;TEntityType&gt;(Lambda idFieldExpression, string nameSingular, string namePlural, string description, string iconSingular, string iconPlural, Lambda collectionConfig = null) *: FluidityCollectionConfig&lt;TEntityType&gt;*
{: .signature}

Adds a collection to the current tree with the given names, description and icons. An ID property accessor expression is required so that Fluidity knows which property is the ID property. See the [Collections API documentation]({{ site.baseurl }}/api/collections/) for more info.

````csharp
// Example
treeConfig.AddCollection<Person>(p => p.Id, "Person", "People", "A collection of people", "icon-umb-users", "icon-umb-users", collectionConfig => {
    ...
});
````
