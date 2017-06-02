---
title: "Ex&#233;cution de comparaisons de cha&#238;nes ind&#233;pendantes de la culture | Microsoft Docs"
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
  - "culture (paramètre)"
  - "opérations de chaînes indépendantes de la culture, comparaisons"
  - "comparaisons de chaînes (.NET Framework), culture indépendante"
  - "String.Compare (méthode)"
  - "String.CompareTo (méthode)"
  - "chaînes (.NET Framework), comparer"
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
caps.latest.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 23
---
# Ex&#233;cution de comparaisons de cha&#238;nes ind&#233;pendantes de la culture
Par défaut, la méthode <xref:System.String.Compare%2A?displayProperty=fullName> effectue des comparaisons dépendantes de la culture et qui respectent la casse.  Cette méthode inclut également plusieurs surcharges qui fournissent un paramètre `culture` qui vous permet de spécifier la culture à utiliser et un paramètre `comparisonType` qui vous sert à spécifier les règles de comparaison à utiliser.  L'appel de ces méthodes au lieu de la surcharge par défaut supprime toute ambiguïté à propos des règles utilisées dans un appel de méthode particulier et indique si une comparaison donnée est dépendante ou indépendante de la culture.  
  
> [!NOTE]
>  Les surcharges de la méthode <xref:System.String.CompareTo%2A?displayProperty=fullName> effectuent des comparaisons dépendantes de la culture et sensibles à la casse ; vous ne pouvez pas utiliser cette méthode pour effectuer des comparaisons indépendantes de la culture.  Pour des raisons de clarté du code, nous recommandons d'utiliser la méthode <xref:System.String.Compare%2A?displayProperty=fullName> à la place.  
  
 Pour les opérations dépendantes de la culture, spécifiez la valeur d'énumération <xref:System.StringComparison?displayProperty=fullName> ou <xref:System.StringComparison?displayProperty=fullName> comme paramètre `comparisonType`.  Si vous souhaitez effectuer une comparaison dépendante de la culture à l'aide d'une culture désignée autre que la culture actuelle, spécifiez l'objet <xref:System.Globalization.CultureInfo> qui représente cette culture comme paramètre `culture` .  
  
 Les comparaisons de chaînes indépendantes de la culture prises en charge par la méthode <xref:System.String.Compare%2A?displayProperty=fullName> sont linguistiques \(selon les conventions de tri de la culture indifférente\) ou non linguistiques \(selon la valeur ordinale des caractères dans la chaîne\).  La plupart des comparaisons de chaînes indépendantes de la culture sont non linguistiques.  Pour ces comparaisons, spécifiez la valeur d'énumération <xref:System.StringComparison?displayProperty=fullName> ou <xref:System.StringComparison?displayProperty=fullName> comme paramètre `comparisonType`.  Par exemple, si une décision de sécurité \(telle qu'une comparaison de nom d'utilisateur ou de mot de passe\) est basée sur le résultat d'une comparaison de chaînes, l'opération doit être indépendante de la culture et non linguistique pour garantir que le résultat n'est pas affecté par les conventions d'une culture ou d'une langue particulière.  
  
 Utilisez la comparaison de chaînes linguistique indépendante de la culture si vous souhaitez gérer de manière cohérente des chaînes linguistiquement pertinentes de cultures multiples.  Par exemple, si votre application affiche des mots qui utilisent plusieurs jeux de caractères dans une zone de liste, vous pouvez afficher des mots dans le même ordre indépendamment de la culture actuelle.  Pour les comparaisons linguistiques indépendantes de la culture, le .NET Framework définit une culture indifférente basée sur les conventions linguistiques de l'anglais.  Pour effectuer une comparaison linguistique indépendante de la culture, spécifiez <xref:System.StringComparison?displayProperty=fullName> ou <xref:System.StringComparison?displayProperty=fullName> comme paramètre `comparisonType`.  
  
 L'exemple suivant exécute deux comparaisons de chaînes indépendantes de la culture, non linguistiques.  La première respecte la casse, mais pas la seconde.  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  
  
## Voir aussi  
 <xref:System.String.Compare%2A?displayProperty=fullName>   
 <xref:System.String.CompareTo%2A?displayProperty=fullName>   
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)   
 [Meilleures pratiques pour l'utilisation de chaînes](../../../docs/standard/base-types/best-practices-strings.md)