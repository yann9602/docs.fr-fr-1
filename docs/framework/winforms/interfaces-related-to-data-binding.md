---
title: "Interfaces participant &#224; la liaison de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "données (Windows Forms), interfaces de liaison de données"
  - "liaison de données, interfaces"
  - "IBindingList (interface), liaison de données Windows Forms"
  - "IBindingListView (interface)"
  - "IDataErrorInfo (interface), liaison de données Windows Forms"
  - "IEditableObject (interface), liaison de données Windows Forms"
  - "IList (interface), liaison de données Windows Forms"
  - "INotifyPropertyChanged (interface)"
  - "interfaces, liaison de données Windows Forms"
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Interfaces participant &#224; la liaison de donn&#233;es
Avec [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], vous pouvez créer de nombreuses structures de données différentes pour répondre aux besoins de liaison de votre application et des données avec lesquelles vous travaillez.  Vous pouvez créer vos propres classes qui fournissent ou consomment des données dans les Windows Forms.  Ces objets peuvent offrir divers niveaux de fonctionnalités et de complexité, de la liaison de données de base à la prise en charge du mode design, la vérification des erreurs, la notification des modifications et même une prise en charge de la restauration structurée des modifications apportées aux données elles\-mêmes.  
  
## Consommateurs d'interfaces de liaison de données  
 Les sections suivantes décrivent deux groupes d'objets d'interface.  Le premier groupe rassemble les interfaces qui sont implémentées sur les sources de données par les auteurs de source de données.  Ces interfaces sont conçues pour être consommées par les consommateurs de source de données qui sont, dans la plupart des cas, des contrôles ou des composants Windows Forms.  Le second groupe répertorie les interfaces conçues pour être utilisées par les auteurs du composant.  Les auteurs du composant utilisent ces interfaces lorsqu'ils créent un composant qui prend en charge la liaison de données à consommer par le moteur de liaison de données Windows Forms.  Vous pouvez implémenter ces interfaces dans les classes associées à votre formulaire pour activer la liaison de données ; chaque cas présente une classe qui implémente une interface qui active l'interaction avec les données.  Les outils d'expérience de design de données avec développement rapide d'application \(RAD, Rapid Application Development\) de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] tirent déjà parti de ces fonctionnalités.  
  
### Interfaces pour implémentation par des auteurs de source de données  
 Les interfaces suivantes sont conçues pour être consommées par des contrôles Windows Forms :  
  
-   l'interface <xref:System.Collections.IList>.  
  
     Une classe qui implémente l'interface <xref:System.Collections.IList> peut être un <xref:System.Array>, <xref:System.Collections.ArrayList> ou <xref:System.Collections.CollectionBase>.  Il s'agit de listes indexées d'éléments de type <xref:System.Object>.  Ces listes doivent contenir des types homogènes, car le premier élément de l'index détermine le type.  <xref:System.Collections.IList> serait uniquement disponible pour la liaison au moment de l'exécution.  
  
    > [!NOTE]
    >  Si vous souhaitez créer une liste d'objets métier à lier à des Windows Forms, envisagez d'utiliser le <xref:System.ComponentModel.BindingList%601>.  Le <xref:System.ComponentModel.BindingList%601> est une classe extensible qui implémente les interfaces principales requises pour la liaison de données Windows Forms bidirectionnelle.  
  
-   l'interface <xref:System.ComponentModel.IBindingList>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IBindingList> offre un niveau plus élevé de fonctionnalités de liaison de données.  Cette implémentation fournit des fonctions de tri de base et la notification des modifications à la fois lorsque les éléments de la liste changent \(par exemple, le troisième élément présente un changement dans le champ Adresse dans une liste de clients\), et lorsque la liste elle\-même change \(par exemple, le nombre d'éléments de la liste augmente ou diminue\).  La notification des modifications est importante si vous prévoyez d'avoir plusieurs contrôles liés aux mêmes données et que vous souhaitez que les changements de données faits dans un des contrôles se propagent aux autres contrôles dépendants.  
  
    > [!NOTE]
    >  La notification de modifications est activée pour l'interface <xref:System.ComponentModel.IBindingList> via la propriété <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> qui, lorsqu'elle est `true`, déclenche un événement <xref:System.ComponentModel.IBindingList.ListChanged>, indiquant que la liste a changé ou qu'un élément de la liste a changé.  
  
     Le type de modification est décrit par la propriété <xref:System.ComponentModel.ListChangedType> du paramètre <xref:System.ComponentModel.ListChangedEventArgs>.  Ainsi, chaque fois que le modèle de données est mis à jour, chaque vue dépendante, comme d'autres contrôles liés à la même source de données, sera également mise à jour.  Toutefois, les objets figurant dans la liste doivent avertir la liste de toute modification dont ils font l'objet afin que celle\-ci puisse déclencher l'événement <xref:System.ComponentModel.IBindingList.ListChanged>.  
  
    > [!NOTE]
    >  La <xref:System.ComponentModel.BindingList%601> fournit une implémentation générique de l'interface <xref:System.ComponentModel.IBindingList>.  
  
-   l'interface <xref:System.ComponentModel.IBindingListView>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IBindingListView> fournit toutes les fonctionnalités d'une implémentation de <xref:System.ComponentModel.IBindingList>, ainsi que les fonctionnalités de filtrage et de tri avancées.  Cette implémentation offre le filtrage basé sur chaîne et le tri multicolonne avec paires direction\-descripteur de propriété.  
  
-   l'interface <xref:System.ComponentModel.IEditableObject>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IEditableObject> permet à un objet de déterminer le moment où les modifications apportées à cet objet deviennent permanentes.  Cette implémentation vous permet de recourir aux méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, qui vous autorisent à annuler des modifications apportées à l'objet.  Ci\-après une brève explication du fonctionnement des méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> et de la manière avec laquelle elles fonctionnent les unes avec les autres pour assurer la possibilité d'une restauration des données à leur état initial, après qu'elles aient été modifiées :  
  
    -   La méthode <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> signale le début d'une modification d'un objet.  Un objet qui implémente cette interface devra stocker les éventuelles mises à jour après l'appel de la méthode <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> d'une manière telle que ces mises à jour puissent être annulées en cas d'appel de la méthode <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>.  Dans la liaison de données des Windows Forms, vous pouvez appeler <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> à plusieurs reprises dans le cadre d'une seule et même transaction de modification \(par exemple, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>\).  Les implémentations de <xref:System.ComponentModel.IEditableObject> doivent garder trace d'informations telles que si <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> a déjà été appelé et ignorer les appels ultérieurs à <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.  Dans la mesure où il est possible d'appeler plusieurs fois cette méthode, il est essentiel que les appels suivants de celle\-ci soient non destructeurs ; en d'autres termes, les appels de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> suivants ne peuvent pas détruire les mises à jour effectuées ni modifier les données enregistrées lors du premier appel de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.  
  
    -   La méthode <xref:System.ComponentModel.IEditableObject.EndEdit%2A> envoie toute modification apportée depuis l'appel de <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> à l'objet sous\-jacent, si cet objet est actuellement en mode édition.  
  
    -   La méthode <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> rejette toute modification apportée à l'objet.  
  
     Pour plus d'informations sur les méthodes <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A> et <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, consultez [Enregistrement de données dans des groupes de données](../Topic/Save%20data%20back%20to%20the%20database.md).  
  
     L'aspect transactionnel des fonctionnalités de données est utilisé par le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
-   l'interface <xref:System.ComponentModel.ICancelAddNew>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.ICancelAddNew> implémente habituellement l'interface <xref:System.ComponentModel.IBindingList> et vous permet de restaurer un ajout fait à la source de données avec la méthode <xref:System.ComponentModel.IBindingList.AddNew%2A>.  Si votre source de données implémente l'interface <xref:System.ComponentModel.IBindingList>, veillez à ce qu'elle implémente également l'interface <xref:System.ComponentModel.ICancelAddNew>.  
  
-   l'interface <xref:System.ComponentModel.IDataErrorInfo>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IDataErrorInfo> permet aux objets d'offrir des informations d'erreur personnalisées aux contrôles dépendants :  
  
    -   la propriété <xref:System.ComponentModel.IDataErrorInfo.Error%2A> retourne un message d'erreur général \(par exemple, "Une erreur s'est produite"\).  
  
    -   la propriété <xref:System.ComponentModel.IDataErrorInfo.Item%2A> retourne une chaîne avec le message d'erreur spécifique de la colonne \(par exemple, "La valeur dans la colonne `State`  n'est pas valide"\).  
  
-   l'interface <xref:System.Collections.IEnumerable>.  
  
     Une classe qui implémente l'interface <xref:System.Collections.IEnumerable> est généralement consommée par [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].  La prise en charge par Windows Forms de cette interface est uniquement disponible à travers le composant <xref:System.Windows.Forms.BindingSource>.  
  
    > [!NOTE]
    >  Le composant <xref:System.Windows.Forms.BindingSource> copie tous les éléments <xref:System.Collections.IEnumerable> dans une liste séparée, à des fins de liaison.  
  
-   l'interface <xref:System.ComponentModel.ITypedList>.  
  
     Une classe de collections qui implémente l'interface <xref:System.ComponentModel.ITypedList> offre la possibilité de contrôler l'ordre et le jeu de propriétés exposées au contrôle dépendant.  
  
    > [!NOTE]
    >  Lorsque vous implémentez la méthode <xref:System.ComponentModel.ITypedList.GetItemProperties%2A>, et que le tableau <xref:System.ComponentModel.PropertyDescriptor> n'est pas nul, la dernière entrée dans le tableau sera le descripteur de propriété qui décrit la propriété de liste, qui est une autre liste d'éléments.  
  
-   l'interface <xref:System.ComponentModel.ICustomTypeDescriptor>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.ICustomTypeDescriptor> fournit des informations dynamiques sur elle\-même.  Cette interface est semblable à <xref:System.ComponentModel.ITypedList>, mais est utilisée pour les objets plutôt que les listes.  Cette interface est utilisée par <xref:System.Data.DataRowView> pour projeter le schéma des lignes sous\-jacentes.  Une implémentation simple de <xref:System.ComponentModel.ICustomTypeDescriptor> est fournie par la classe <xref:System.ComponentModel.CustomTypeDescriptor>.  
  
    > [!NOTE]
    >  Pour prendre en charge la liaison au moment du design à des types qui implémentent <xref:System.ComponentModel.ICustomTypeDescriptor>, le type doit également implémenter <xref:System.ComponentModel.IComponent> et exister en tant qu'instance sur le formulaire.  
  
-   l'interface <xref:System.ComponentModel.IListSource>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IListSource> active la liaison basée sur liste sur des objets autres que listes.  La méthode <xref:System.ComponentModel.IListSource.GetList%2A> d'<xref:System.ComponentModel.IListSource> permet de retourner une liste pouvant être liée à partir d'un objet qui n'hérite pas d'<xref:System.Collections.IList>.  <xref:System.ComponentModel.IListSource> est utilisé par la classe <xref:System.Data.DataSet>.  
  
-   l'interface <xref:System.ComponentModel.IRaiseItemChangedEvents>.  
  
     Une classe qui implémente l'interface <xref:System.ComponentModel.IRaiseItemChangedEvents> est une liste pouvant être liée qui implémente également l'interface <xref:System.ComponentModel.IBindingList>.  Cette interface est utilisée pour indiquer si votre type déclenche des événements <xref:System.ComponentModel.IBindingList.ListChanged> de type <xref:System.ComponentModel.ListChangedType> via sa propriété <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>.  
  
    > [!NOTE]
    >  Vous devez implémenter <xref:System.ComponentModel.IRaiseItemChangedEvents> si votre source de données assure la conversion de propriété en liste précédemment décrite et interagit avec le composant <xref:System.Windows.Forms.BindingSource>.  Sinon, le <xref:System.Windows.Forms.BindingSource> exécutera également la conversion de propriété en liste, ce qui entraînera une baisse des performances.  
  
-   l'interface <xref:System.ComponentModel.ISupportInitialize>.  
  
     Un composant qui implémente l'interface <xref:System.ComponentModel.ISupportInitialize> bénéficie des optimisations de lot pour définir les propriétés et initialiser les propriétés co\-dépendantes.  Le <xref:System.ComponentModel.ISupportInitialize> contient deux méthodes :  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> signale que l'initialisation d'objet démarre.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> signale que l'initialisation d'objet se termine.  
  
-   l'interface <xref:System.ComponentModel.ISupportInitializeNotification>.  
  
     Un composant qui implémente l'interface <xref:System.ComponentModel.ISupportInitializeNotification> implémente également l'interface <xref:System.ComponentModel.ISupportInitialize>.  Cette interface vous permet de notifier d'autres composants <xref:System.ComponentModel.ISupportInitialize> que l'initialisation est terminée.  L'interface <xref:System.ComponentModel.ISupportInitializeNotification> contient deux membres :  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> retourne une valeur `boolean` indiquant si le composant est initialisé.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> se produit lorsque <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> est appelé.  
  
-   l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
     Une classe qui implémente cette interface est un type qui déclenche un événement lorsqu'une de ses valeurs de propriété change.  Cette interface est conçue pour remplacer le schéma obligeant à avoir un événement de modification pour chaque propriété d'un contrôle.  Utilisé dans un <xref:System.ComponentModel.BindingList%601>, un objet métier doit implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged> et le BindingList'1 convertira des événements <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> en événements <xref:System.ComponentModel.BindingList%601.ListChanged> de type <xref:System.ComponentModel.ListChangedType>.  
  
    > [!NOTE]
    >  Pour que la notification de modifications se produise entre un client lié et une source de données, votre type de source\-donnée liée doit implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged> \(de préférence\) ou vous fournissez les événements *propertyName*`Changed` pour le type dépendant, mais vous ne pouvez pas faire les deux à la fois.  
  
### Interfaces pour implémentation par des auteurs de composants  
 Les interfaces suivantes sont conçues pour être consommées par le moteur de liaison de données Windows Forms :  
  
-   l'interface <xref:System.Windows.Forms.IBindableComponent>.  
  
     Une classe qui implémente cette interface est un composant non\-contrôle qui prend en charge la liaison de données.  Cette classe retourne les liaisons de données et le contexte de liaison du composant à travers les propriétés <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> et <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> de cette interface.  
  
    > [!NOTE]
    >  Si votre composant hérite de <xref:System.Windows.Forms.Control>, vous n'avez pas besoin d'implémenter l'interface <xref:System.Windows.Forms.IBindableComponent>.  
  
-   l'interface <xref:System.Windows.Forms.ICurrencyManagerProvider>.  
  
     Une classe qui implémente l'interface <xref:System.Windows.Forms.ICurrencyManagerProvider> est un composant qui fournit son propre <xref:System.Windows.Forms.CurrencyManager> pour gérer les liaisons associées à ce composant particulier.  L'accès au <xref:System.Windows.Forms.CurrencyManager> personnalisé est assuré par la propriété <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>.  
  
    > [!NOTE]
    >  Une classe qui hérite de <xref:System.Windows.Forms.Control> gère automatiquement les liaisons à travers sa propriété <xref:System.Windows.Forms.Control.BindingContext%2A>, ce qui signifie que les cas dans lesquels vous devez implémenter le <xref:System.Windows.Forms.ICurrencyManagerProvider> sont assez rares.  
  
## Voir aussi  
 [Liaison de données et Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [Comment : créer un contrôle à liaison simple dans un Windows Form](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)   
 [Liaison de données Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)