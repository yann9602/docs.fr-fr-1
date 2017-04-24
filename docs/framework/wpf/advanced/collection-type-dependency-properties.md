---
title: "Propri&#233;t&#233;s de d&#233;pendance de type collection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propriétés de type de collection"
  - "propriétés de dépendance"
  - "propriétés, type de collection"
  - "propriétés, dependency"
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Propri&#233;t&#233;s de d&#233;pendance de type collection
Cette rubrique propose des conseils et des modèles suggérés pour l'implémentation d'une [propriété de dépendance](GTMT) de type collection.  
  
   
  
<a name="implementing"></a>   
## Implémentation d'une propriété de dépendance de type collection  
 Dans le cas d'une propriété de dépendance, le modèle d'implémentation que vous suivez consiste généralement à définir un wrapper de propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], dans lequel cette propriété est soutenue par un identificateur <xref:System.Windows.DependencyProperty> plutôt que par un champ ou une autre construction.  Vous devez suivre ce même modèle lorsque vous implémentez une propriété de type collection.  Une propriété de type collection ajoute toutefois une certaine complexité au modèle lorsque le type contenu dans la collection est lui\-même une classe dérivée <xref:System.Windows.DependencyObject> ou <xref:System.Windows.Freezable>.  
  
<a name="initializing"></a>   
## Initialisation de la collection au\-delà de la valeur par défaut  
 Lorsque vous créez une propriété de dépendance, vous ne spécifiez pas sa valeur par défaut comme étant la valeur de champ initiale.  Vous la spécifiez à l'aide des métadonnées de la propriété de dépendance.  Si votre propriété est un type référence, la valeur par défaut spécifiée dans les métadonnées de la propriété de dépendance n'est pas une valeur par défaut par instance, mais bien une valeur par défaut qui s'applique à toutes les instances du type.  Par conséquent, vous devez prendre garde de ne pas utiliser la collection statique unique définie par les métadonnées de la propriété de type collection comme valeur par défaut active pour les nouvelles instances créées de votre type.  À la place, vous devez vous assurer que vous affectez délibérément à la valeur de collection une collection \(instance\) unique dans le cadre de votre logique de constructeur de classe.  Sinon, vous créerez une classe singleton involontaire.  
  
 Prenons l'exemple suivant.  La section suivante de l'exemple illustre la définition d'une classe `Aquarium`.  Cette classe définit la propriété de dépendance de type dépendance `AquariumObjects`, qui utilise le type <xref:System.Collections.Generic.List%601> générique avec une contrainte de type <xref:System.Windows.FrameworkElement>.  Dans l'appel <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> à la propriété de dépendance, les métadonnées stipulent que la valeur par défaut sera une nouvelle <xref:System.Collections.Generic.List%601> générique.  
  
 <!-- TODO: review snippet reference [!code-csharp[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemdefinition)]  -->
 [!code-vb[PropertiesOvwSupport#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemdefinition)]  
[!code-csharp[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemendb)]
[!code-vb[PropertiesOvwSupport#CollectionProblemEndB](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemendb)]  
  
 Cependant, si vous laissez le code tel qu'illustré, cette valeur par défaut de liste unique sera partagée pour toutes les instances d'`Aquarium`.  Si vous avez exécuté le code de test suivant, qui a pour but de vous montrer comment instancier deux instances d'`Aquarium` distinctes et ajouter un `Fish` différent à chacune, vous risquez d'être surpris par le résultat :  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Au lieu d'avoir deux collections contenant chacune une unité, vous avez deux collections de deux unités \!  En effet, chaque `Aquarium` a ajouté son `Fish` à la collection de valeurs par défaut, car il n'y a eu qu'un seul appel de constructeur dans les métadonnées, lequel a par conséquent été partagé entre toutes les instances.  Ce n'est sans doute pas ce que vous vouliez.  
  
 Pour résoudre ce problème, vous devez réinitialiser la valeur de la propriété de dépendance de type collection à une instance unique, dans le cadre de l'appel de constructeur de classe.  Comme la propriété est une propriété de dépendance en lecture seule, utilisez la méthode <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> pour la définir, à l'aide du <xref:System.Windows.DependencyPropertyKey> qui est uniquement accessible dans la classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Si vous exécutez à nouveau ce même code de test, vous obtiendrez un résultat plus prévisible, où chaque `Aquarium` prend en charge sa propre collection unique.  
  
 Il peut y avoir une légère variation à ce modèle si vous choisissez d'avoir votre propriété de collection en lecture\-écriture.  Dans ce cas, vous pouvez appeler l'accesseur set public du constructeur pour l'initialisation, ce qui aura toujours pour effet d'appeler la signature non\-clé de <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> dans votre wrapper défini à l'aide d'un identificateur <xref:System.Windows.DependencyProperty> public.  
  
## Signalement des modifications des valeurs de liaison des propriétés de collection  
 Une propriété de collection qui est elle\-même une propriété de dépendance ne signale pas automatiquement les modifications apportées à ses sous\-propriétés.  Si vous créez des liaisons au sein d'une collection, cela peut empêcher la liaison de signaler les modifications et, de ce fait, invalider certains scénarios de liaison de données.  Cependant, si vous utilisez le type collection <xref:System.Windows.FreezableCollection%601>, les modifications de sous\-propriétés apportées aux éléments contenus dans la collection sont correctement signalées et la liaison donne les résultats escomptés.  
  
 Pour activer la liaison de sous\-propriétés dans une collection d'objets de dépendance, créez la propriété de collection en tant que type <xref:System.Windows.FreezableCollection%601>, avec une contrainte de type pour cette collection à toute classe dérivée <xref:System.Windows.DependencyObject>.  
  
## Voir aussi  
 <xref:System.Windows.FreezableCollection%601>   
 [XAML et classes personnalisées pour WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)