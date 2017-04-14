---
title: "Architecture du composant BindingSource | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingSource (composant Windows Forms), à propos du composant BindingSource"
  - "BindingSource (composant), architecture"
  - "liaison de données, BindingSource (composant)"
  - "Windows Forms, liaison de données"
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Architecture du composant BindingSource
À l'aide du composant <xref:System.Windows.Forms.BindingSource>, vous pouvez lier universellement tous les contrôles Windows Forms aux sources de données.  
  
 Le composant <xref:System.Windows.Forms.BindingSource> simplifie le processus de liaison des contrôles à une source de données et offre des avantages par rapport à la liaison de données traditionnelle :  
  
-   Il active la liaison aux objets métier au moment du design.  
  
-   Il encapsule les fonctionnalités <xref:System.Windows.Forms.CurrencyManager> et expose les événements <xref:System.Windows.Forms.CurrencyManager> au moment du design.  
  
-   Il simplifie la création d'une liste qui prend en charge l'interface <xref:System.ComponentModel.IBindingList> en fournissant une notification de modifications de liste pour les sources de données qui ne prennent pas en charge la notification de modifications de liste en mode natif.  
  
-   Il fournit un point d'extensibilité pour la méthode <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=fullName>.  
  
-   Il fournit un niveau d'indirection entre la source de données et le contrôle.  Cette indirection est essentielle lorsque la source de données change au moment de l'exécution.  
  
-   Il interagit avec d'autres contrôles Windows Forms liés aux données, en particulier les contrôles <xref:System.Windows.Forms.BindingNavigator> et <xref:System.Windows.Forms.DataGridView>.  
  
 Pour ces raisons, le composant <xref:System.Windows.Forms.BindingSource> est la meilleure façon de lier vos contrôles Windows Forms aux sources de données.  
  
## Fonctions BindingSource  
 Le composant <xref:System.Windows.Forms.BindingSource> fournit plusieurs fonctionnalités pour lier les contrôles aux données.  Grâce à ces fonctionnalités, vous pouvez implémenter la plupart des scénarios de liaison de données avec un minimum de codage de votre part.  
  
 Le composant <xref:System.Windows.Forms.BindingSource> s'en charge via une interface cohérente permettant d'accéder à un grand nombre de sources de données différentes.  Cela signifie que vous utilisez la même procédure pour effectuer des liaisons aux différents types.  Par exemple, vous pouvez attacher la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> à <xref:System.Data.DataSet> ou à un objet métier et, dans les deux cas, vous utilisez le même jeu de propriétés, de méthodes et d'événements pour manipuler la source de données.  
  
 L'interface cohérente fournie par le composant <xref:System.Windows.Forms.BindingSource> simplifie grandement le processus de liaison des données aux contrôles.  Pour les types de sources de données qui fournissent la notification de modifications, le composant <xref:System.Windows.Forms.BindingSource> communique automatiquement les modifications entre le contrôle et la source de données.  Pour les types de source de données qui ne proposent pas de notification de modifications, les événements vous permettant de générer des notifications de modifications sont fournis.  La liste suivante affiche les fonctionnalités prises en charge par le composant <xref:System.Windows.Forms.BindingSource> :  
  
-   Indirection.  
  
-   Gestion des devises.  
  
-   Source de données en tant que liste.  
  
-   <xref:System.Windows.Forms.BindingSource> en tant que <xref:System.ComponentModel.IBindingList>.  
  
-   Création d'éléments personnalisés.  
  
-   Création d'éléments transactionnels.  
  
-   Prise en charge <xref:System.Collections.IEnumerable>.  
  
-   Prise en charge au moment du design  
  
-   Méthodes <xref:System.Windows.Forms.ListBindingHelper> statiques.  
  
-   Tri et filtrage avec l'interface <xref:System.ComponentModel.IBindingListView>.  
  
-   Intégration à <xref:System.Windows.Forms.BindingNavigator>.  
  
### Adressage indirect  
 Le composant <xref:System.Windows.Forms.BindingSource> fournit un niveau d'indirection entre un contrôle et une source de données.  Au lieu de lier directement un contrôle à une source de données, vous liez le contrôle à <xref:System.Windows.Forms.BindingSource> et attachez la source de données à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> du composant <xref:System.Windows.Forms.BindingSource>.  
  
 Avec ce niveau d'indirection, vous pouvez modifier la source de données sans réinitialiser la liaison du contrôle.  Cela vous permet de bénéficier des fonctions suivantes :  
  
-   Vous pouvez attacher <xref:System.Windows.Forms.BindingSource> à des sources de données différentes tout en conservant les liaisons de contrôle actuelles.  
  
-   Vous pouvez modifier des éléments de la source de données et notifier des contrôles liés.  Pour plus d'informations, consultez [Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Vous pouvez effectuer la liaison à <xref:System.Type> et non à un objet en mémoire.  Pour plus d'informations, consultez [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  Vous pouvez ensuite effectuer une liaison à un objet au moment de l'exécution.  
  
### Gestion des devises  
 Le composant <xref:System.Windows.Forms.BindingSource> implémente l'interface <xref:System.Windows.Forms.ICurrencyManagerProvider> afin de procéder à la gestion des devises à votre place.  À l'aide de l'interface <xref:System.Windows.Forms.ICurrencyManagerProvider>, vous pouvez également accéder au gestionnaire de devise pour un <xref:System.Windows.Forms.BindingSource> et au gestionnaire de devise pour un autre <xref:System.Windows.Forms.BindingSource> lié au même <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 Le composant <xref:System.Windows.Forms.BindingSource> encapsule les fonctionnalités <xref:System.Windows.Forms.CurrencyManager> et expose les événements et propriétés <xref:System.Windows.Forms.CurrencyManager> les plus communs.  Le tableau suivant décrit quelques\-uns des membres relatifs à la gestion des devises.  
  
 Propriété <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>  
 Permet d'obtenir le gestionnaire de devises associé à <xref:System.Windows.Forms.BindingSource>.  
  
 Méthode <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>  
 S'il existe un autre <xref:System.Windows.Forms.BindingSource> lié à la donnée membre spécifiée, permet d'obtenir son gestionnaire de devises.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Current%2A>  
 Obtient l'élément actuel de la source de données.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Position%2A>  
 Obtient ou définit la position actuelle au sein de la liste sous\-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.EndEdit%2A>  
 Applique des modifications en attente à la source de données sous\-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>  
 Annule l'opération de modification actuelle.  
  
### Source de données en tant que liste.  
 Le composant <xref:System.Windows.Forms.BindingSource> implémente les interfaces <xref:System.ComponentModel.IBindingListView> et <xref:System.ComponentModel.ITypedList>.  Avec cette implémentation, vous pouvez utiliser le composant <xref:System.Windows.Forms.BindingSource> lui\-même comme source de données, sans stockage externe.  
  
 Lorsque le composant <xref:System.Windows.Forms.BindingSource> est attaché à une source de données, il expose la source de données comme une liste.  
  
 Vous pouvez affecter à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> plusieurs sources de données.  Celles\-ci incluent les types, les objets et les listes de types.  La source de données résultante sera exposée en tant que liste.  Le tableau suivant affiche certaines des sources de données courantes et l'évaluation de liste résultante.  
  
|DataSource, propriété|Résultats de la liste|  
|---------------------------|---------------------------|  
|Référence Null \(`Nothing` en Visual Basic\)|<xref:System.ComponentModel.IBindingList> vide d'objets.  L'ajout d'un élément affecte à la liste le type de l'élément ajouté.|  
|Référence null \(`Nothing` dans Visual Basic\) avec le jeu <xref:System.Windows.Forms.BindingSource.DataMember%2A>|Non pris en charge ; déclenche <xref:System.ArgumentException>.|  
|Type autre que liste ou objet de type "T"|<xref:System.ComponentModel.IBindingList> vide de type "T".|  
|Instance de tableau|<xref:System.ComponentModel.IBindingList> contenant les éléments du tableau.|  
|Instance <xref:System.Collections.IEnumerable>|<xref:System.ComponentModel.IBindingList> contenant les éléments <xref:System.Collections.IEnumerable>|  
|Instance de liste contenant le type "T"|Instance <xref:System.ComponentModel.IBindingList> contenant le type "T".|  
  
 De plus, vous pouvez affecter à <xref:System.Windows.Forms.BindingSource.DataSource%2A> d'autres types de listes, tels que <xref:System.ComponentModel.IListSource> et <xref:System.ComponentModel.ITypedList>, et le <xref:System.Windows.Forms.BindingSource> les gèrera de manière appropriée.  Dans ce cas, le type contenu dans la liste doit avoir un constructeur par défaut.  
  
### BindingSource en tant que IBindingList  
 Le composant <xref:System.Windows.Forms.BindingSource> fournit des membres pour l'accès aux données sous\-jacentes et leur manipulation en tant que <xref:System.ComponentModel.IBindingList>.  Le tableau suivant décrit quelques\-uns de ces membres.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.List%2A>|Permet d'obtenir la liste qui résulte de l'évaluation des propriétés <xref:System.Windows.Forms.BindingSource.DataSource%2A> ou <xref:System.Windows.Forms.BindingSource.DataMember%2A>.|  
|Méthode <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Ajoute un nouvel élément à la liste sous\-jacente.  S'applique aux sources de données qui implémentent l'interface <xref:System.ComponentModel.IBindingList> et autorisent l'ajout d'éléments \(c'est\-à\-dire que la propriété <xref:System.Windows.Forms.BindingSource.AllowNew%2A> a la valeur `true`\).|  
  
### Création d'éléments personnalisés  
 Vous pouvez gérer l'événement <xref:System.Windows.Forms.BindingSource.AddingNew> pour fournir votre propre logique de création d'éléments.  L'événement <xref:System.Windows.Forms.BindingSource.AddingNew> se produit avant l'ajout d'un nouvel objet à <xref:System.Windows.Forms.BindingSource>.  Cet événement est déclenché après l'appel à la méthode <xref:System.Windows.Forms.BindingSource.AddNew%2A>, mais avant l'ajout du nouvel élément à la liste sous\-jacente.  En gérant cet événement, vous pouvez fournir le comportement de création d'éléments personnalisés sans dérivation de la classe <xref:System.Windows.Forms.BindingSource>.  Pour plus d'informations, consultez [Comment : personnaliser l'ajout d'éléments avec le composant BindingSource Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### Création d'éléments transactionnels  
 Le composant <xref:System.Windows.Forms.BindingSource> implémente l'interface <xref:System.ComponentModel.ICancelAddNew>, qui active la création d'éléments transactionnels.  Après avoir créé provisoirement un élément en appelant <xref:System.Windows.Forms.BindingSource.AddNew%2A>, l'ajout peut être validé ou annulé en procédant des façons suivantes :  
  
-   La méthode <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> validera explicitement l'ajout en attente.  
  
-   L'exécution d'une autre opération de collection, telle qu'une insertion, une suppression ou un déplacement, validera implicitement l'ajout en attente.  
  
-   La méthode <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> annulera l'ajout en attente s'il n'a pas déjà été validé.  
  
### Prise en charge d'IEnumerable  
 Le composant <xref:System.Windows.Forms.BindingSource> permet la liaison de contrôles aux sources de données <xref:System.Collections.IEnumerable>.  Avec ce composant, vous pouvez effectuer une liaison à une source de données, telle que <xref:System.Data.SqlClient.SqlDataReader?displayProperty=fullName>.  
  
 Lorsqu'une source de données <xref:System.Collections.IEnumerable> est assignée au composant <xref:System.Windows.Forms.BindingSource>, <xref:System.Windows.Forms.BindingSource> crée <xref:System.ComponentModel.IBindingList> et ajoute le contenu de la source de données <xref:System.Collections.IEnumerable> à la liste.  
  
### Prise en charge au moment du design  
 Certains types d'objets ne peuvent pas être créés au moment du design, tels que des objets créés à partir d'une classe de fabrique ou des objets retournés par un service Web.  Vous serez parfois amené à lier vos contrôles à ces types au moment du design, même si aucun objet auquel vos contrôles peuvent être liés n'est en mémoire.  Par exemple, vous pouvez avoir besoin d'étiqueter les en\-têtes de colonnes d'un contrôle <xref:System.Windows.Forms.DataGridView> avec les noms des propriétés publiques du type personnalisé.  
  
 Pour prendre en charge ce scénario, le composant <xref:System.Windows.Forms.BindingSource> prend en charge la liaison à <xref:System.Type>.  Lorsque vous assignez <xref:System.Type> à la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A>, le composant <xref:System.Windows.Forms.BindingSource> crée un <xref:System.ComponentModel.BindingList%601> vide d'éléments <xref:System.Type>.  Les contrôles que vous liez par la suite au composant <xref:System.Windows.Forms.BindingSource> seront informés de la présence des propriétés ou du schéma de votre type au moment du design ou au moment de l'exécution.  Pour plus d'informations, consultez [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### Méthodes ListBindingHelper statiques  
 Les types <xref:System.Windows.Forms.BindingContext?displayProperty=fullName>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=fullName> et <xref:System.Windows.Forms.BindingSource> partagent la logique commune pour générer une liste à partir d'une paire `DataSource`\/`DataMember`.  De plus, cette logique commune est exposée publiquement en vue d'être utilisée par les auteurs du contrôle et d'autres tiers dans les méthodes `static` suivantes :  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### Tri et filtrage avec l'interface IBindingListView  
 Le composant <xref:System.Windows.Forms.BindingSource> implémente l'interface <xref:System.ComponentModel.IBindingListView>, qui étend l'interface <xref:System.ComponentModel.IBindingList>.  Le <xref:System.ComponentModel.IBindingList> offre le tri de colonne simple et le <xref:System.ComponentModel.IBindingListView> offre le tri et le filtrage avancés.  À l'aide de <xref:System.ComponentModel.IBindingListView>, vous pouvez trier et filtrer des éléments dans la source de données, si celle\-ci implémente également l'une de ces interfaces.  Le composant <xref:System.Windows.Forms.BindingSource> ne fournit pas d'implémentation de référence de ces membres.  À la place, les appels sont envoyés à la liste sous\-jacente.  
  
 Le tableau suivant décrit les propriétés que vous utilisez pour trier et filtrer.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.Filter%2A>|Si la source de données est <xref:System.ComponentModel.IBindingListView>, obtient ou définit l'expression utilisée pour filtrer les lignes affichées.|  
|Propriété <xref:System.Windows.Forms.BindingSource.Sort%2A>|Si la source de données est <xref:System.ComponentModel.IBindingList>, obtient ou définit un nom de colonne utilisé pour le tri et pour les informations sur l'ordre de tri.<br /><br /> ou<br /><br /> Si la source de données est <xref:System.ComponentModel.IBindingListView> et prend en charge le tri avancé, obtient plusieurs noms de colonnes utilisés pour le tri et l'ordre de tri.|  
  
### Intégration à BindingNavigator  
 Vous pouvez utiliser le composant <xref:System.Windows.Forms.BindingSource> pour lier tous les contrôles Windows Forms à une source de données, mais le contrôle <xref:System.Windows.Forms.BindingNavigator> est conçu spécifiquement pour être utilisé avec le composant <xref:System.Windows.Forms.BindingSource>.  Le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit une interface utilisateur permettant de contrôler l'élément actuel du composant <xref:System.Windows.Forms.BindingSource>.  Par défaut, le contrôle <xref:System.Windows.Forms.BindingNavigator> fournit des boutons qui correspondent aux méthodes de navigation sur le composant <xref:System.Windows.Forms.BindingSource>.  Pour plus d'informations, consultez [Comment : naviguer parmi les données avec le contrôle BindingNavigator Windows Forms](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.BindingNavigator>   
 [Vue d'ensemble du composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)   
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)