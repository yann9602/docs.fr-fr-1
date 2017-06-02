---
title: "Comment&#160;: &#233;num&#233;rer les fuseaux horaires d&#39;un ordinateur | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fuseaux horaires (énumération dans le .NET Framework)"
  - "fuseaux horaires (.NET Framework), énumérer"
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: &#233;num&#233;rer les fuseaux horaires d&#39;un ordinateur
Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant.  Les systèmes d'exploitation Windows XP et Windows Vista stockent ces informations dans le Registre.  Toutefois, bien qu'il existe de nombreux fuseaux horaires dans le monde, le Registre contient des informations relatives à un sous\-ensemble de fuseaux horaires uniquement.  De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement.  En conséquence, un fuseau horaire particulier ne peut pas toujours être défini ni disponible sur un système.  Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient d'abord de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l'utilisateur une liste des fuseaux horaires.  Il faut donc qu'une application énumère les fuseaux horaires définis sur un système local.  
  
> [!NOTE]
>  Si une application dépend de la présence d'un fuseau horaire particulier qui n'est pas défini sur un système local, elle peut sérialiser et désérialiser les informations relatives au fuseau horaire.  Le fuseau horaire peut ensuite être ajouté à un contrôle de liste pour que l'utilisateur de l'application puisse le sélectionner.  Pour plus d'informations, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).  
  
### Pour énumérer les fuseaux horaires présents sur le système local  
  
1.  Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName>.  La méthode retourne une collection <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> générique d'objets <xref:System.TimeZoneInfo>.  Les entrées dans la collection sont triées par leur propriété <xref:System.TimeZoneInfo.DisplayName%2A>.  Par exemple :  
  
     [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
     [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]  
  
2.  Énumérez les objets <xref:System.TimeZoneInfo> individuels dans la collection en utilisant une boucle `foreach` \(en C\#\) ou `For Each`…`Next` \(dans Visual Basic\) et exécutez tous les traitements nécessaires sur chaque objet.  Par exemple, le code suivant énumère la collection <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> d'objets <xref:System.TimeZoneInfo> retournée à l'étape 1 et affiche le nom complet de chaque fuseau horaire sur la console.  
  
     [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
     [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]  
  
### Pour fournir à l'utilisateur une liste des fuseaux horaires présents sur le système local  
  
1.  Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName>.  La méthode retourne une collection <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> générique d'objets <xref:System.TimeZoneInfo>.  
  
2.  Assignez la collection retournée à l'étape 1 à la propriété `DataSource` d'un contrôle de liste Windows Forms ou ASP.NET.  
  
3.  Récupérez l'objet <xref:System.TimeZoneInfo> que l'utilisateur a sélectionné.  
  
 L'exemple suivant utilise une application Windows pour illustrer cette situation.  
  
## Exemple  
 Une application Windows qui affiche les fuseaux horaires définis sur un système dans une zone de liste est lancée.  Une boîte de dialogue s'affiche ensuite ; elle contient la valeur de la propriété <xref:System.TimeZoneInfo.DisplayName%2A> de l'objet de fuseau horaire sélectionné par l'utilisateur .  
  
 [!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
 [!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]  
  
 La plupart des contrôles de liste \(tels que le contrôle <xref:System.Windows.Forms.ListBox?displayProperty=fullName> ou <xref:System.Web.UI.WebControls.BulletedList?displayProperty=fullName> \) vous permettent d'assigner une collection de variables objet à leur propriété `DataSource` tant que cette collection implémente l'interface <xref:System.Collections.IEnumerable>. \(C'est le cas pour la classe générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.\). Pour afficher un objet individuel dans la collection, le contrôle appelle la méthode `ToString` correspondante afin d'extraire la chaîne utilisée pour représenter l'objet.  Dans le cas d'objets <xref:System.TimeZoneInfo>, la méthode `ToString` retourne le nom complet de l'objet <xref:System.TimeZoneInfo> \(la valeur de sa propriété <xref:System.TimeZoneInfo.DisplayName%2A>\).  
  
> [!NOTE]
>  Comme les contrôles de liste appellent la méthode `ToString` d'un objet, vous pouvez assigner une collection d'objets <xref:System.TimeZoneInfo> au contrôle, afficher un nom explicite pour chaque objet et récupérer l'objet <xref:System.TimeZoneInfo> que l'utilisateur a sélectionné.  Il n'est donc plus nécessaire d'extraire une chaîne pour chaque objet dans la collection, d'assigner la chaîne à une collection qui est assignée à son tour à la propriété `DataSource` du contrôle, de récupérer la chaîne que l'utilisateur a sélectionnée, puis d'utiliser cette chaîne pour extraire l'objet qu'il décrit.  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   qu'une référence à System.Core.dll soit ajoutée au projet ;  
  
-   que les espaces de noms suivants soient importés :  
  
     <xref:System> \(en code C\#\)  
  
     <xref:System.Collections.ObjectModel>  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)   
 [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)   
 [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)