---
title: "Propriétés de dépendance de type collection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], dependency
- properties [WPF], collection-type
- dependency properties [WPF]
- collection-type properties [WPF]
ms.assetid: 99f96a42-3ab7-4f64-a16b-2e10d654e97c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11927efee2b8375550767d119e6b4a95b3ef7bd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="collection-type-dependency-properties"></a>Propriétés de dépendance de type collection
Cette rubrique propose des conseils et des modèles suggérés pour l’implémentation d’une propriété de dépendance de type collection.  
  
 
  
<a name="implementing"></a>   
## <a name="implementing-a-collection-type-dependency-property"></a>Implémentation d’une propriété de dépendance de type collection  
 Pour une propriété de dépendance en général, le modèle d’implémentation que vous suivez est que vous définissez un [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] wrapper de propriété, où cette propriété est soutenue par un <xref:System.Windows.DependencyProperty> identificateur au lieu d’un champ ou une autre construction. Vous devez suivre ce même modèle quand vous implémentez une propriété de type collection. Toutefois, une propriété de type collection présente une complexité au modèle chaque fois que le type qui est inclu dans la collection est lui-même une <xref:System.Windows.DependencyObject> ou <xref:System.Windows.Freezable> classe dérivée.  
  
<a name="initializing"></a>   
## <a name="initializing-the-collection-beyond-the-default-value"></a>Initialisation de la collection au-delà de la valeur par défaut  
 Quand vous créez une propriété de dépendance, vous ne spécifiez pas sa valeur par défaut comme étant la valeur de champ initiale. Vous la spécifiez à l’aide des métadonnées de la propriété de dépendance. Si votre propriété est un type référence, la valeur par défaut spécifiée dans les métadonnées de la propriété de dépendance n’est pas une valeur par défaut par instance, mais bien une valeur par défaut qui s’applique à toutes les instances du type. Ainsi, vous devez prendre garde de ne pas utiliser la collection statique unique définie par les métadonnées de la propriété de type collection comme valeur par défaut active pour les instances créées de votre type. À la place, vous devez vous assurer que vous affectez délibérément à la valeur de collection une collection (instance) unique dans le cadre de votre logique de constructeur de classe. Sinon, vous créerez une classe singleton involontaire.  
  
 Prenons l'exemple suivant. La section suivante de l’exemple illustre la définition d’une classe `Aquarium`. La classe définit la propriété de dépendance de type collection `AquariumObjects`, qui utilise le type générique <xref:System.Collections.Generic.List%601> type avec un <xref:System.Windows.FrameworkElement> contrainte de type. Dans le <xref:System.Windows.DependencyProperty.Register%28System.String%2CSystem.Type%2CSystem.Type%2CSystem.Windows.PropertyMetadata%29> appel à la propriété de dépendance, les métadonnées établit la valeur par défaut est un nouveau type générique <xref:System.Collections.Generic.List%601>.  
  
 [!code-csharp[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport2/CSharp/page.xaml.cs#collectionproblemdefinition)]
 [!code-vb[PropertiesOvwSupport2#CollectionProblemDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport2/visualbasic/page.xaml.vb#collectionproblemdefinition)]  
  
 Cependant, si vous laissez le code tel qu’illustré, cette valeur par défaut de liste unique est partagée pour toutes les instances d’`Aquarium`. Si vous avez exécuté le code de test suivant, qui a pour but de vous montrer comment instancier deux instances d’`Aquarium` distinctes et ajouter un `Fish` différent à chacune, vous risquez d’être surpris par le résultat :  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemtestcode)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemTestCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemtestcode)]  
  
 Au lieu d’avoir deux collections contenant chacune une unité, vous avez deux collections de deux unités ! En effet, chaque `Aquarium` a ajouté son `Fish` à la collection de valeurs par défaut, car il n’y a eu qu’un seul appel de constructeur dans les métadonnées, lequel a donc été partagé entre toutes les instances. Ce n’est sans doute pas ce que vous vouliez.  
  
 Pour résoudre ce problème, vous devez réinitialiser la valeur de la propriété de dépendance de type collection à une instance unique, dans le cadre de l’appel de constructeur de classe. Étant donné que la propriété est une propriété de dépendance en lecture seule, vous utilisez la <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyPropertyKey%2CSystem.Object%29> méthode pour la définir, à l’aide de la <xref:System.Windows.DependencyPropertyKey> qui est uniquement accessible dans la classe.  
  
 [!code-csharp[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#collectionproblemctor)]
 [!code-vb[PropertiesOvwSupport#CollectionProblemCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#collectionproblemctor)]  
  
 Si vous exécutez à nouveau ce même code de test, vous obtiendrez un résultat plus prévisible, où chaque `Aquarium` prend en charge sa propre collection unique.  
  
 Il peut y avoir une légère variation à ce modèle si vous choisissez d’avoir votre propriété de collection en lecture-écriture. Dans ce cas, vous pouvez appeler l’accesseur set public du constructeur pour l’initialisation, ce qui aura toujours être appeler la signature non-clé de <xref:System.Windows.DependencyObject.SetValue%28System.Windows.DependencyProperty%2CSystem.Object%29> dans votre wrapper défini, à l’aide d’un public <xref:System.Windows.DependencyProperty> identificateur.  
  
## <a name="reporting-binding-value-changes-from-collection-properties"></a>Signalement des modifications des valeurs de liaison des propriétés de collection  
 Une propriété de collection qui est elle-même une propriété de dépendance ne signale pas automatiquement les modifications apportées à ses sous-propriétés. Si vous créez des liaisons au sein d’une collection, cela peut empêcher la liaison de signaler les modifications et, de ce fait, invalider certains scénarios de liaison de données. Toutefois, si vous utilisez le type de collection <xref:System.Windows.FreezableCollection%601> comme type de collection, puis les modifications de sous-propriétés apportées aux éléments contenus dans la collection sont correctement signalées et la liaison fonctionne comme prévu.  
  
 Pour activer la liaison de sous-propriétés dans une collection d’objets de dépendance, créez la propriété de collection en tant que type <xref:System.Windows.FreezableCollection%601>, avec une contrainte de type pour cette collection à toute <xref:System.Windows.DependencyObject> classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.FreezableCollection%601>  
 [XAML et classes personnalisées pour WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)
