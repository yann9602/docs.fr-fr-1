---
title: "Comment&#160;: supprimer des caract&#232;res non valides d&#39;une cha&#238;ne | Microsoft Docs"
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
  - "expressions régulières, exemples"
  - "nettoyer une chaîne d'entrée"
  - "entrée utilisateur, exemples"
  - ".NET Framework (expressions régulières), exemples"
  - "expressions régulières (.NET Framework), exemples"
  - "Regex.Replace (méthode)"
  - "supprimer les caractères non valides"
  - "Replace (méthode)"
  - "valider les entrées d'utilisateur"
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: supprimer des caract&#232;res non valides d&#39;une cha&#238;ne
L'exemple suivant utilise la méthode statique <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> pour supprimer des caractères non valides d'une chaîne.  
  
## Exemple  
 Vous pouvez utiliser la méthode `CleanInput` définie dans cet exemple pour supprimer des caractères potentiellement nuisibles entrés dans un champ de texte qui accepte les entrées de l'utilisateur.  Dans ce cas, `CleanInput` retourne la chaîne qui reste après suppression de tous les caractères non alphanumériques à l'exception des points \(.\), des symboles @ et des tirets \(\-\).  Vous pouvez toutefois modifier le modèle d'expression régulière afin qu'il supprime tous les caractères qui ne doivent pas être inclus dans la chaîne d'entrée.  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 Le modèle d'expression régulière `[^\w\.@-]` correspond à tout caractère qui n'est pas un caractère alphabétique, un point, un symbole @ ou un tiret.  Un caractère alphabétique est une lettre, un chiffre décimal ou un connecteur de ponctuation tel qu'un trait de soulignement.  Tout caractère qui correspond à ce modèle est remplacé par <xref:System.String.Empty?displayProperty=fullName>, qui est la chaîne définie par le modèle de remplacement.  Pour autoriser les caractères spéciaux dans les entrées d'utilisateur, ajoutez\-les à la classe de caractères dans le modèle d'expression régulière.  Par exemple, le modèle d'expression régulière `[^\w\.@-\\%]` autorise également un symbole de pourcentage et une barre oblique inverse dans une chaîne d'entrée.  
  
## Voir aussi  
 [Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)