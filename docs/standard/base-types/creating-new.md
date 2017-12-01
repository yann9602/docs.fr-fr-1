---
title: "Création de nouvelles chaînes dans .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a>Création de nouvelles chaînes dans .NET
Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] permet des chaînes à l’aide d’une assignation simple et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide d’un nombre de paramètres différents. Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit également plusieurs méthodes dans la <xref:System.String?displayProperty=nameWithType> classe créer la nouvelle chaîne en combinant plusieurs chaînes, tableaux de chaînes, des objets ou des objets.  
  
## <a name="creating-strings-using-assignment"></a>Création de chaînes à l’aide d’une affectation  
 Le moyen le plus simple pour créer un nouveau <xref:System.String> objet consiste à assigner un littéral de chaîne en un <xref:System.String> objet.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Création de chaînes à l’aide d’un constructeur de classe  
 Vous pouvez utiliser les surcharges de la <xref:System.String> constructeur de classe pour créer des chaînes à partir des tableaux de caractères. Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.  
  
## <a name="methods-that-return-strings"></a>Méthodes retournant des chaînes  
 Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.  
  
|Nom de la méthode|Utilisation|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Génère des chaînes à partir de deux ou de plusieurs chaînes.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Génère une nouvelle chaîne en combinant un tableau de chaînes.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.|  
  
### <a name="format"></a>Format  
 Vous pouvez utiliser la **String.Format** pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets. Cette méthode convertit automatiquement tout objet passé en une chaîne. Par exemple, si votre application doit afficher une **Int32** valeur et un **DateTime** valeur à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la **Format**(méthode). Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).  
  
 L’exemple suivant utilise le **Format** méthode pour créer une chaîne qui utilise une variable de type entier.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Dans cet exemple,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> affiche la date et l’heure de la manière spécifiée par la culture associée au thread actuel.  
  
### <a name="concat"></a>Concat  
 Le **String.Concat** méthode peut être utilisée pour créer facilement un nouvel objet string à partir de deux ou plusieurs objets existants. Elle offre un moyen de concaténer des chaînes indépendamment du langage. Cette méthode accepte toute classe qui dérive de **System.Object**. L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 Le **String.Join** méthode crée une nouvelle chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation. Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.  
  
 L’exemple suivant utilise un espace pour lier un tableau de chaînes.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 Le **String.Insert** méthode crée une nouvelle chaîne en insérant une chaîne dans une position spécifiée dans une autre chaîne. Cette méthode utilise un index de base zéro. L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 Le **String.CopyTo** méthode copie d’une chaîne dans un tableau de caractères. Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier. Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier. Tous les index sont de base zéro.  
  
 L’exemple suivant utilise le **CopyTo** méthode pour copier les caractères du mot « Hello » à partir d’une chaîne de l’objet à la première position d’index d’un tableau de caractères.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)  
 [Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md)
