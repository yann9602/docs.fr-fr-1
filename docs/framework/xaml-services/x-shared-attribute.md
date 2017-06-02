---
title: "x:Shared Attribute | Microsoft Docs"
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
  - "XAML [XAML Services], x:Shared attribute"
  - "x:Shared attribute [XAML Services]"
  - "Shared attribute in XAML [XAML Services]"
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 16
---
# x:Shared Attribute
Quand la valeur est définie sur `false`, modifie le comportement de récupération des ressources WPF de manière à ce que les requêtes des ressources attribuées créent une nouvelle instance pour chaque requête, au lieu de partager la même instance pour toutes les requêtes.  
  
## Utilisation d'attributs XAML  
  
```  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## Notes  
 `x:Shared` est mappé dans l'espace de noms XAML du langage XAML et est reconnu comme un élément de langage XAML valide par les services XAML .NET Framework et ses lecteurs XAML.  Toutefois, les fonctions déclarées de `x:Shared` sont uniquement pertinentes pour les applications WPF, et pour l'analyseur XAML WPF.  Dans WPF, `x:Shared` est uniquement utile comme attribut en cas d'application à un objet qui existe dans un <xref:System.Windows.ResourceDictionary> WPF.  Les autres utilisations ne lèvent pas d'exceptions d'analyse ou d'autres erreurs, mais elles n'ont aucun effet.  
  
 La signification de `x:Shared` n'est pas spécifiée dans la spécification de langage XAML.  Les autres implémentations XAML, telles que celles qui génèrent à partir des services XAML .NET Framework, ne fournissent pas nécessairement une prise en charge des partages de ressources.  Ces implémentations XAML peuvent utiliser la même approche dans l'infrastructure de support qui utilise également des valeurs `x:Shared`.  
  
 Dans WPF, la condition `x:Shared` par défaut pour les ressources est `true`.  Cette condition signifie que toute demande de ressource retourne toujours la même instance.  
  
 La ressource d'origine change en cas de modification d'un objet retourné via une API de ressource <xref:System.Windows.FrameworkElement.FindResource%2A> ou de modification directe d'un objet dans un <xref:System.Windows.ResourceDictionary>.  Si les références à cette ressource étaient des références de ressource dynamiques, les consommateurs de cette ressource obtiendront la ressource modifiée.  
  
 \(Si les références à la ressource étaient des références de ressource statiques, les modifications apportées à la ressource après le temps de traitement [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] sont sans importance.  Pour plus d'informations sur les références de ressources dynamiques et statiques, consultez [Ressources XAML](../../../ocs/framework/wpf/advanced/xaml-resources.md).  
  
 La spécification explicite de `x:Shared="true"` est rare effectuée parce que c'est déjà la valeur par défaut.  Il n'y a aucun équivalent direct de code pour `x:Shared` dans le modèle d'objet WPF ; il peut être spécifié uniquement dans une utilisation de XAML et doit être traité soit par le comportement WPF par défaut, soit dans un flux de nœud XAML intermédiaire sur le chemin d'accès du chargement, si le traitement est effectué à l'aide des services XAML .NET Framework et des lecteurs XAML.  
  
 Un scénario pour `x:Shared="false"` consiste à définir une classe dérivée <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> en tant que ressource et ensuite introduire la ressource d'élément dans un modèle de contenu.  `x:Shared="false"` active une ressource d'élément à introduire plusieurs fois dans la même collection \(par exemple <xref:System.Windows.Controls.UIElementCollection>\).  Sans `x:Shared="false"` ce n'est pas valide car la collection impose l'unicité de son contenu.  Toutefois, le comportement de `x:Shared="false"` crée une autre instance identique de la ressource au lieu de retourner la même instance.  
  
 Un autre scénario pour `x:Shared="false"` consiste à utiliser une ressource <xref:System.Windows.Freezable> pour les valeurs d'animation, mais à modifier la ressource par animation.  
  
 La manipulation de chaînes `false` ne respecte pas la casse.  
  
 Dans WPF `x:Shared`, est uniquement valide sous les conditions suivantes :  
  
-   <xref:System.Windows.ResourceDictionary> qui contient les éléments avec `x:Shared` doit être compilé.  <xref:System.Windows.ResourceDictionary> ne peut pas être en XAML libre ou utilisé pour des thèmes.  
  
-   <xref:System.Windows.ResourceDictionary> qui contient les éléments ne doit pas être imbriqué dans un autre <xref:System.Windows.ResourceDictionary>.  Par exemple, vous ne pouvez pas utiliser `x:Shared` pour les éléments dans un <xref:System.Windows.ResourceDictionary> qui est dans un <xref:System.Windows.Style> qui est déjà un élément <xref:System.Windows.ResourceDictionary>.  
  
## Voir aussi  
 <xref:System.Windows.ResourceDictionary>   
 [Ressources XAML](../../../ocs/framework/wpf/advanced/xaml-resources.md)   
 [Éléments de base](../../../ocs/framework/wpf/advanced/base-elements.md)