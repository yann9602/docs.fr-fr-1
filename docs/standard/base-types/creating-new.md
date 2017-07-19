---
title: "Cr&#233;ation de nouvelles cha&#238;nes dans .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Concat (méthode)"
  - "CopyTo (méthode)"
  - "Format (méthode)"
  - "Insert (méthode)"
  - "Join (méthode)"
  - "chaînes (.NET Framework), créer"
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Cr&#233;ation de nouvelles cha&#238;nes dans .NET Framework
Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] permet de créer des chaînes à l'aide d'une assignation simple et surcharge un constructeur de classe pour la prise en charge de la création de chaînes à l'aide de différents paramètres.  Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]fournit également plusieurs méthodes dans la classe <xref:System.String?displayProperty=fullName> qui créent des objets String en combinant plusieurs chaînes, tableaux de chaînes ou objets.  
  
## Création de chaînes à l'aide d'une assignation  
 Le moyen le plus simple de créer un objet <xref:System.String> consiste à assigner un littéral de chaîne à un objet <xref:System.String>.  
  
## Création de chaînes à l'aide d'un constructeur de classe  
 Vous pouvez utiliser les surcharges du constructeur de classe <xref:System.String> pour créer des chaînes à partir de tableaux de caractères.  Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.  
  
## Méthodes retournant des chaînes  
 Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.  
  
|Nom de la méthode|Utilisation|  
|-----------------------|-----------------|  
|<xref:System.String.Format%2A?displayProperty=fullName>|Construit une chaîne mise en forme à partir d'un jeu d'objets en entrée.|  
|<xref:System.String.Concat%2A?displayProperty=fullName>|Construit des chaînes à partir de deux ou plusieurs chaînes.|  
|<xref:System.String.Join%2A?displayProperty=fullName>|Construit une nouvelle chaîne en combinant un tableau de chaînes.|  
|<xref:System.String.Insert%2A?displayProperty=fullName>|Construit une nouvelle chaîne en insérant une chaîne dans l'index spécifié d'une chaîne existante.|  
|<xref:System.String.CopyTo%2A?displayProperty=fullName>|Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.|  
  
### Format  
 Vous pouvez utiliser la méthode **String.Format** pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets.  Cette méthode convertit automatiquement tout objet passé en une chaîne.  Par exemple, si votre application doit afficher une valeur **Int32** et une valeur **DateTime** pour l'utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l'aide de la méthode **Format**.  Pour plus d'informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section sur la [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).  
  
 L'exemple suivant utilise la méthode **Format** pour créer une chaîne utilisant une variable de type integer.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 Dans cet exemple, <xref:System.DateTime.Now%2A?displayProperty=fullName> affiche la date et l'heure actuelles de la manière spécifiée par la culture associée au thread en cours.  
  
### Concat  
 La méthode **String.Concat** peut être utilisée pour créer aisément un nouvel objet chaîne au départ de deux ou plusieurs objets existants.  Elle fournit une façon de concaténer des chaînes indépendamment de la langue.  Cette méthode accepte toute classe qui dérive de **System.Object**.  L'exemple suivant crée une chaîne à partir de deux objets string existants et un caractère de délimitation.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### Join  
 La méthode **String.Join** crée une nouvelle chaîne à partir d'un tableau de chaînes et d'une chaîne de séparateur.  Cette méthode est utile pour concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.  
  
 L'exemple suivant utilise un espace pour former un tableau de chaînes.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### Insert  
 La méthode **String.Insert** crée une nouvelle chaîne en insérant une chaîne dans une position spécifiée dans une autre chaîne.  Cette méthode utilise un index de base zéro.  L'exemple suivant insère une chaîne dans la cinquième position d'index de `MyString` et crée une nouvelle chaîne avec cette valeur.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### CopyTo  
 La méthode **String.CopyTo** copie des fragments d'une chaîne dans un tableau de caractères.  Vous pouvez spécifier l'index de début de la chaîne et le nombre de caractères à copier.  Cette méthode utilise l'index de la source, un tableau de caractères, l'index de destination et le nombre de caractères à copier.  Tous les index sont de base zéro.  
  
 L'exemple suivant utilise la méthode **CopyTo** pour copier les caractères du mot "Hello" à partir d'un objet chaîne vers la première position d'un tableau de caractères.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## Voir aussi  
 [Opérations de chaînes de base](../../../docs/standard/base-types/basic-string-operations.md)   
 [Mise en forme composite](../../../docs/standard/base-types/composite-formatting.md)