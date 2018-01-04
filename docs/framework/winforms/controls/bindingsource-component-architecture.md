---
title: Architecture du composant BindingSource
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25a69f31d8da8638cfc92ff94d8f90dbcb327158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component-architecture"></a>Architecture du composant BindingSource
Avec le <xref:System.Windows.Forms.BindingSource> composant, vous pouvez lier universellement tous les contrôles Windows Forms aux sources de données.  
  
 Le <xref:System.Windows.Forms.BindingSource> composant simplifie le processus de liaison de contrôles à une source de données et fournit les avantages suivants sur la liaison de données traditionnelle :  
  
-   Active la liaison au moment du design à des objets métier.  
  
-   Encapsule <xref:System.Windows.Forms.CurrencyManager> fonctionnalité et expose <xref:System.Windows.Forms.CurrencyManager> événements au moment du design.  
  
-   Simplifie la création d’une liste qui prend en charge la <xref:System.ComponentModel.IBindingList> interface en fournissant une notification de modification de liste de notification de modification de sources de données qui ne prennent pas en mode natif en charge liste.  
  
-   Fournit un point d’extensibilité pour la <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> (méthode).  
  
-   Fournit un niveau d’indirection entre la source de données et le contrôle. Cette indirection est essentielle lorsque la source de données peut modifier au moment de l’exécution.  
  
-   Interagit avec d’autres contrôles Windows Forms liés aux données, en particulier le <xref:System.Windows.Forms.BindingNavigator> et <xref:System.Windows.Forms.DataGridView> contrôles.  
  
 Pour ces raisons, le <xref:System.Windows.Forms.BindingSource> composant est la meilleure façon de lier vos contrôles Windows Forms aux sources de données.  
  
## <a name="bindingsource-features"></a>Fonctionnalités de BindingSource  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit plusieurs fonctionnalités de liaison des contrôles aux données. Avec ces fonctionnalités, vous pouvez implémenter la plupart des scénarios de liaison de données presque sans codage de votre part.  
  
 Le <xref:System.Windows.Forms.BindingSource> composant accomplit cela en fournissant une interface cohérente permettant d’accéder à nombreux types de sources de données. Cela signifie que vous utilisez la même procédure pour la liaison à n’importe quel type. Par exemple, vous pouvez attacher le <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété un <xref:System.Data.DataSet> ou à un objet métier et dans les deux cas, vous utilisez le même jeu de propriétés, méthodes et événements pour manipuler la source de données.  
  
 L’interface cohérente fournie par le <xref:System.Windows.Forms.BindingSource> composant simplifie considérablement le processus de liaison de données aux contrôles. Pour les types de source de données qui assurent la notification de modifications, le <xref:System.Windows.Forms.BindingSource> composant communique automatiquement les modifications entre le contrôle et la source de données. Pour les types de source de données qui ne fournissent pas de notification de modification, les événements sont fournies pour vous permettre de générer des notifications de modification. La liste suivante affiche les fonctionnalités prises en charge par le <xref:System.Windows.Forms.BindingSource> composant :  
  
-   Indirection.  
  
-   Gestion des devises.  
  
-   Source de données sous forme de liste.  
  
-   <xref:System.Windows.Forms.BindingSource>comme un <xref:System.ComponentModel.IBindingList>.  
  
-   Création d’éléments personnalisés.  
  
-   Création d’éléments transactionnels.  
  
-   <xref:System.Collections.IEnumerable>prise en charge.  
  
-   Prise en charge de la conception.  
  
-   Statique <xref:System.Windows.Forms.ListBindingHelper> méthodes.  
  
-   Tri et filtrage avec le <xref:System.ComponentModel.IBindingListView> interface.  
  
-   Intégration avec <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Adressage indirect  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit un niveau d’indirection entre un contrôle et une source de données. Au lieu de lier un contrôle directement à une source de données, vous liez le contrôle à un <xref:System.Windows.Forms.BindingSource>, et vous connectez à la source de données pour le <xref:System.Windows.Forms.BindingSource> du composant <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété.  
  
 Avec ce niveau d’indirection, vous pouvez modifier la source de données sans réinitialiser la liaison du contrôle. Ceci vous donne les possibilités suivantes :  
  
-   Vous pouvez attacher le <xref:System.Windows.Forms.BindingSource> à différentes sources de données tout en conservant les liaisons de contrôle en cours.  
  
-   Vous pouvez modifier des éléments dans la source de données et notifier des contrôles liés. Pour plus d’informations, consultez [Comment : refléter la mises à jour de Source de données dans un contrôle Windows Forms avec le BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Vous pouvez lier à un <xref:System.Type> au lieu d’un objet en mémoire. Pour plus d’informations, consultez [Comment : lier un contrôle Windows Forms à un Type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md). Vous pouvez ensuite la lier à un objet en cours d’exécution.  
  
### <a name="currency-management"></a>Gestion des devises  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente la <xref:System.Windows.Forms.ICurrencyManagerProvider> permettant de gérer la gestion des devises pour vous. Avec la <xref:System.Windows.Forms.ICurrencyManagerProvider> interface, vous pouvez également accéder au Gestionnaire de devise pour un <xref:System.Windows.Forms.BindingSource>, le Gestionnaire de devise pour une autre <xref:System.Windows.Forms.BindingSource> liés au même <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 Le <xref:System.Windows.Forms.BindingSource> composant encapsule <xref:System.Windows.Forms.CurrencyManager> expose les plus courants et les fonctionnalités <xref:System.Windows.Forms.CurrencyManager> propriétés et événements. Le tableau suivant décrit certains des membres liés à la gestion des devises.  
  
 Propriété <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>  
 Obtient le Gestionnaire de devise associé à la <xref:System.Windows.Forms.BindingSource>.  
  
 Méthode <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>  
 S’il existe un autre <xref:System.Windows.Forms.BindingSource> lié au membre de données spécifié, obtient son gestionnaire de devise.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Current%2A>  
 Obtient l'élément actuel de la source de données.  
  
 Propriété <xref:System.Windows.Forms.BindingSource.Position%2A>  
 Obtient ou définit la position actuelle dans la liste sous-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.EndEdit%2A>  
 Applique des modifications en attente à la source de données sous-jacente.  
  
 Méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>  
 Annule l'opération de modification actuelle.  
  
### <a name="data-source-as-a-list"></a>Source de données sous forme de liste  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente la <xref:System.ComponentModel.IBindingListView> et <xref:System.ComponentModel.ITypedList> interfaces. Avec cette implémentation, vous pouvez utiliser le <xref:System.Windows.Forms.BindingSource> composant lui-même en tant que source de données, sans stockage externe.  
  
 Lorsque le <xref:System.Windows.Forms.BindingSource> composant est attaché à une source de données, il expose la source de données sous forme de liste.  
  
 Le <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété peut être définie à plusieurs sources de données. Notamment, les types, les objets et les listes de types. La source de données résultant sera exposée sous forme de liste. Le tableau suivant répertorie certaines des sources de données courantes et l’évaluation de la liste résultante.  
  
|Propriété de source de données|Résultats de la liste|  
|-------------------------|------------------|  
|Référence Null (`Nothing` en Visual Basic)|Vide <xref:System.ComponentModel.IBindingList> d’objets. Ajout d’un élément de définit la liste pour le type de l’élément ajouté.|  
|Une référence null (`Nothing` en Visual Basic) avec <xref:System.Windows.Forms.BindingSource.DataMember%2A> défini|Non pris en charge ; déclenche <xref:System.ArgumentException>.|  
|Type non-liste ou objet de type « T »|Vide <xref:System.ComponentModel.IBindingList> de type « T ».|  
|Instance de tableau|Un <xref:System.ComponentModel.IBindingList> contenant les éléments du tableau.|  
|<xref:System.Collections.IEnumerable>instance|Un <xref:System.ComponentModel.IBindingList> contenant le <xref:System.Collections.IEnumerable> éléments|  
|Instance de liste contenant type « T »|Un <xref:System.ComponentModel.IBindingList> instance contenant le type « T ».|  
  
 En outre, <xref:System.Windows.Forms.BindingSource.DataSource%2A> peut être définie à d’autres types de liste, tels que <xref:System.ComponentModel.IListSource> et <xref:System.ComponentModel.ITypedList>et le <xref:System.Windows.Forms.BindingSource> les gérer en conséquence. Dans ce cas, le type de contenu dans la liste doit avoir un constructeur par défaut.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>Composant BindingSource comme un IBindingList  
 Le <xref:System.Windows.Forms.BindingSource> composant fournit des membres pour accéder et manipuler les données sous-jacentes comme un <xref:System.ComponentModel.IBindingList>. Le tableau suivant décrit quelques-unes de ces membres.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.List%2A>|Obtient la liste des résultats de l’évaluation de la <xref:System.Windows.Forms.BindingSource.DataSource%2A> ou <xref:System.Windows.Forms.BindingSource.DataMember%2A> propriétés.|  
|Méthode <xref:System.Windows.Forms.BindingSource.AddNew%2A>|Ajoute un nouvel élément à la liste sous-jacente. S’applique aux sources de données qui implémentent la <xref:System.ComponentModel.IBindingList> interface et autoriser l’ajout d’éléments (autrement dit, le <xref:System.Windows.Forms.BindingSource.AllowNew%2A> est définie sur `true`).|  
  
### <a name="custom-item-creation"></a>Création d’éléments personnalisés  
 Vous pouvez gérer le <xref:System.Windows.Forms.BindingSource.AddingNew> événement afin de fournir votre propre logique de création d’éléments. Le <xref:System.Windows.Forms.BindingSource.AddingNew> événement se produit avant qu’un nouvel objet est ajouté à la <xref:System.Windows.Forms.BindingSource>. Cet événement est déclenché après la <xref:System.Windows.Forms.BindingSource.AddNew%2A> méthode est appelée, mais avant que le nouvel élément est ajouté à la liste sous-jacente. En gérant cet événement, vous pouvez fournir le comportement de la création d’élément personnalisé sans dériver à partir de la <xref:System.Windows.Forms.BindingSource> classe. Pour plus d’informations, consultez [Comment : personnaliser Ajout d’éléments avec le composant BindingSource Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Création d’éléments transactionnels  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente la <xref:System.ComponentModel.ICancelAddNew> interface, ce qui permet la création d’éléments transactionnels. Une fois un nouvel élément est provisoirement créé à l’aide d’un appel à <xref:System.Windows.Forms.BindingSource.AddNew%2A>, l’ajout peut être validé ou restauré comme suit :  
  
-   Le <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> méthode explicitement validera l’ajout en attente.  
  
-   Effectuer une autre opération de collection, par exemple une insertion, suppression ou déplacement, validera implicitement l’ajout en attente.  
  
-   Le <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> méthode annule l’ajout en attente si la méthode n’a pas encore été validée.  
  
### <a name="ienumerable-support"></a>Prise en charge d’IEnumerable  
 Le <xref:System.Windows.Forms.BindingSource> composant permet de lier des contrôles à <xref:System.Collections.IEnumerable> des sources de données. Avec ce composant, vous pouvez lier à une source de données comme un <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Lorsqu’un <xref:System.Collections.IEnumerable> source de données est affectée à la <xref:System.Windows.Forms.BindingSource> composant, le <xref:System.Windows.Forms.BindingSource> crée un <xref:System.ComponentModel.IBindingList> et ajoute le contenu de la <xref:System.Collections.IEnumerable> source de données à la liste.  
  
### <a name="design-time-support"></a>Prise en charge au moment du design  
 Certains types d’objet ne peut pas être créés au moment du design, telles que les objets créés à partir d’une classe de fabrique ou des objets retournés par un service Web. Vous devrez peut-être parfois lier vos contrôles à ces types au moment du design, même s’il n’existe aucun objet en mémoire, ce qui peuvent se lier vos contrôles. Vous devrez, par exemple, peut-être étiqueter les en-têtes de colonne d’un <xref:System.Windows.Forms.DataGridView> contrôle avec les noms des propriétés publiques de votre type personnalisé.  
  
 Pour prendre en charge ce scénario, le <xref:System.Windows.Forms.BindingSource> composant prend en charge la liaison à un <xref:System.Type>. Lorsque vous assignez un <xref:System.Type> à la <xref:System.Windows.Forms.BindingSource.DataSource%2A> propriété, le <xref:System.Windows.Forms.BindingSource> composant crée vide <xref:System.ComponentModel.BindingList%601> de <xref:System.Type> éléments. Les contrôles que vous liez par la suite à la <xref:System.Windows.Forms.BindingSource> serez alerté de la présence des propriétés ou du schéma de votre type de composant au moment du design ou au moment de l’exécution. Pour plus d’informations, consultez [Comment : lier un contrôle Windows Forms à un Type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Méthodes ListBindingHelper statiques  
 Le <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, et <xref:System.Windows.Forms.BindingSource> types partagent la logique commune pour générer une liste d’un `DataSource` / `DataMember` paire. De plus, cette logique commune est exposée publiquement pour une utilisation par les auteurs de contrôle et d’autres tiers dans l’exemple suivant `static` méthodes :  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Tri et filtrage avec l’Interface IBindingListView  
 Le <xref:System.Windows.Forms.BindingSource> composant implémente la <xref:System.ComponentModel.IBindingListView> interface, ce qui étend la <xref:System.ComponentModel.IBindingList> interface. Le <xref:System.ComponentModel.IBindingList> offre le tri de colonne unique et <xref:System.ComponentModel.IBindingListView> offres advanced triée et filtrée. Avec <xref:System.ComponentModel.IBindingListView>, vous pouvez trier et filtrer les éléments de la source de données, si la source de données également implémente l’une de ces interfaces. Le <xref:System.Windows.Forms.BindingSource> composant ne fournit pas une implémentation de référence de ces membres. Au lieu de cela, les appels sont transférés à la liste sous-jacente.  
  
 Le tableau suivant décrit les propriétés que vous utilisez pour le tri et le filtrage.  
  
|Membre|Description|  
|------------|-----------------|  
|Propriété <xref:System.Windows.Forms.BindingSource.Filter%2A>|Si la source de données est un <xref:System.ComponentModel.IBindingListView>, obtient ou définit l'expression utilisée pour filtrer les lignes affichées.|  
|Propriété <xref:System.Windows.Forms.BindingSource.Sort%2A>|Si la source de données est un <xref:System.ComponentModel.IBindingList>, obtient ou définit un nom de colonne utilisé pour le tri et les informations d'ordre de tri.<br /><br /> - ou -<br /><br /> Si la source de données est un <xref:System.ComponentModel.IBindingListView> et prend en charge tri avancé, obtient plusieurs noms de colonnes utilisés pour le tri et l’ordre de tri|  
  
### <a name="integration-with-bindingnavigator"></a>Intégration à BindingNavigator  
 Vous pouvez utiliser la <xref:System.Windows.Forms.BindingSource> composant à lier n’importe quel contrôle Windows Forms à une source de données, mais la <xref:System.Windows.Forms.BindingNavigator> contrôle est conçu spécifiquement pour fonctionner avec le <xref:System.Windows.Forms.BindingSource> composant. Le <xref:System.Windows.Forms.BindingNavigator> contrôle fournit une interface utilisateur pour le contrôle du <xref:System.Windows.Forms.BindingSource> élément actuel du composant. Par défaut, le <xref:System.Windows.Forms.BindingNavigator> contrôle fournit des boutons qui correspondent aux méthodes de navigation sur le <xref:System.Windows.Forms.BindingSource> composant. Pour plus d’informations, consultez [Comment : parcourir les données avec le contrôle BindingNavigator Windows Forms](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Vue d'ensemble du composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Comment : lier un contrôle Windows Forms à un type](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Comment : répercuter des mises à jour de source de données dans un contrôle Windows Forms avec le BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
