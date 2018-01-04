---
title: x:Shared, attribut
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9cc5e2bff9cc2591c7a12630da5422dbf73713a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xshared-attribute"></a>x:Shared, attribut
Lorsque la valeur `false`, modifie le comportement de récupération des ressources WPF afin que les requêtes des ressources attribuées créent une nouvelle instance pour chaque demande au lieu de partager la même instance pour toutes les demandes.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Notes  
 `x:Shared`est mappé à l’espace de noms XAML du langage XAML et est reconnu comme un élément de langage XAML valid par les Services XAML .NET Framework et ses lecteurs XAML. Toutefois, les fonctions déclarées de `x:Shared` sont uniquement pertinentes pour les applications WPF et pour l’analyseur XAML WPF. Dans WPF, `x:Shared` n’est plus utile en tant qu’attribut lorsqu’il est appliqué à un objet qui existe dans WPF <xref:System.Windows.ResourceDictionary>. Autres utilisations ne lèvent pas d’exceptions d’analyse ou d’autres erreurs, mais elles n’ont aucun effet.  
  
 La signification de `x:Shared` n’est pas spécifié dans la spécification du langage XAML. Autres implémentations XAML, tels que ceux qui s’appuient sur les Services XAML .NET Framework, ne fournissent pas nécessairement le partage des ressources de prise en charge. Ces implémentations XAML peut fournir un comportement similaire dans l’infrastructure de prise en charge qui utilise également `x:Shared` valeurs.  
  
 Dans WPF, la valeur par défaut `x:Shared` condition de ressources est `true`. Cette condition signifie que toute demande de ressource retourne toujours la même instance.  
  
 Modification d’un objet qui est retourné via une API de ressource telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, ou la modification d’un objet directement au sein d’un <xref:System.Windows.ResourceDictionary>, la ressource d’origine change. Si les références à cette ressource étaient des références de ressources dynamiques, les consommateurs de cette ressource obtiendront la ressource modifiée.  
  
 Si les références à la ressource étaient des références de ressources statiques, les modifications à la ressource après [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] le temps de traitement sont sans importance. Pour plus d’informations sur les statiques et les références de ressources dynamiques, consultez [ressources XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Spécification explicite `x:Shared="true"` est rarement fait, car il s’agit déjà la valeur par défaut. S’il n’existe aucun code directe équivalent pour `x:Shared` modèle d’objet dans WPF ; il peut uniquement être spécifié dans une utilisation de XAML et doit être traité par le comportement WPF par défaut ou dans un flux de nœud XAML intermédiaire sur le chemin de chargement si traité à l’aide de .NET Framework XAML Se des services et ses lecteurs XAML.  
  
 Un scénario pour `x:Shared="false"` consiste à définir un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> dérivée de la classe en tant que ressource et puis vous introduisez la ressource d’élément dans un modèle de contenu. `x:Shared="false"`permet à une ressource d’élément à introduire plusieurs fois dans la même collection (par exemple un <xref:System.Windows.Controls.UIElementCollection>). Sans `x:Shared="false"` cela n’est pas valide, car la collection impose l’unicité de son contenu. Toutefois, le `x:Shared="false"` comportement crée une autre instance identique de la ressource au lieu de retourner la même instance.  
  
 Un autre scénario de `x:Shared="false"` si vous utilisez un <xref:System.Windows.Freezable> ressource pour les valeurs d’animation, mais vous souhaitez modifier la ressource par animation.  
  
 La manipulation de chaînes `false` ne respecte pas la casse.  
  
 Dans WPF, `x:Shared` n’est valide que dans les conditions suivantes :  
  
-   Le <xref:System.Windows.ResourceDictionary> qui contient les éléments avec `x:Shared` doit être compilé. Le <xref:System.Windows.ResourceDictionary> ne peut pas être en XAML libre ou utilisé pour des thèmes.  
  
-   Le <xref:System.Windows.ResourceDictionary> qui contient les éléments ne doit pas être imbriqué dans un autre <xref:System.Windows.ResourceDictionary>. Par exemple, vous ne pouvez pas utiliser `x:Shared` pour les éléments dans un <xref:System.Windows.ResourceDictionary> qui se trouve dans un <xref:System.Windows.Style> qui est déjà un <xref:System.Windows.ResourceDictionary> élément.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.ResourceDictionary>  
 [Ressources XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Éléments de base](../../../docs/framework/wpf/advanced/base-elements.md)
