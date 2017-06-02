---
title: "Conventions d’affectation de noms g&#233;n&#233;rales | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "noms (.NET Framework), les conflits"
  - "noms de types, les conflits"
  - "noms de types propres au langage"
  - "noms (.NET Framework), sur les règles de dénomination"
  - "noms (.NET Framework), abréviations"
  - "règles de dénomination abréviation"
  - "règles de dénomination acronyme"
  - "Notation hongroise"
  - "noms (.NET Framework), noms de types"
  - "noms (.NET Framework), acronymes"
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Conventions d’affectation de noms g&#233;n&#233;rales
Cette section décrit d’affectation de noms conventions générales relatives au choix des mots, les instructions sur l’utilisation des abréviations et des acronymes et des recommandations sur la façon d’éviter d’utiliser des noms spécifiques au langage.  
  
## Choix des mots  
 **✓ faire** choisir des noms d’identificateurs lisibles.  
  
 Par exemple, une propriété nommée `HorizontalAlignment` est plus anglais\-lisible que `AlignmentHorizontal`.  
  
 **✓ faire** favoriser la lisibilité par souci de concision.  
  
 Nom de la propriété `CanScrollHorizontally` est meilleure que `ScrollableX` \(une référence à l’axe des x\).  
  
 **X ne pas** utiliser des traits de soulignement, des traits d’union ou d’autres caractères non alphanumériques.  
  
 **X ne pas** utilisent la notation hongroise.  
  
 **X éviter** à l’aide d’identificateurs qui entrent en conflit avec les mots clés de largement utilisé des langages de programmation.  
  
 En fonction de la règle 4 de la Common Language Specification \(CLS\), tous les langages conformes doivent offrir un mécanisme qui permet d’accéder à des éléments nommés qui utilisent un mot clé de cette langue comme identificateur. En c\#, par exemple, utilise le signe comme un mécanisme d’échappement dans ce cas @. Toutefois, il est toujours une bonne idée pour éviter les mots clés communs, car il est beaucoup plus difficile d’utiliser une méthode avec la séquence d’échappement à l’autre sans.  
  
## À l’aide des abréviations et des acronymes  
 **X ne pas** utiliser des abréviations ou contractions comme faisant partie des noms d’identificateur.  
  
 Par exemple, utilisez `GetWindow` plutôt que `GetWin`.  
  
 **X ne pas** utilisez un acronyme qui n’est pas largement acceptées et même si elles sont uniquement lorsque cela est nécessaire.  
  
## Prévention des noms spécifiques au langage  
 **✓ faire** utiliser des noms sémantiquement intéressants plutôt que des mots clés spécifiques au langage pour les noms de type.  
  
 Par exemple, `GetLength` est un nom plus approprié que `GetInt`.  
  
 **✓ faire** utiliser un nom de type CLR générique, plutôt que d’un nom spécifique au langage, dans les rares cas où un identificateur n’a aucune signification sémantique au\-delà de son type.  
  
 Par exemple, une méthode de conversion <xref:System.Int64> doit être nommé `ToInt64`, et non `ToLong` \(étant donné que <xref:System.Int64> est un nom CLR pour c\#\-alias spécifique `long`\). Le tableau suivant présente plusieurs types de base de données utilise les noms des types CLR \(ainsi que les noms de types correspondants pour c\#, Visual Basic et C\+\+\).  
  
|C\#|Visual Basic|C\+\+|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**\_\_int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned \_\_int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Booléen**|**bool**|**Booléen**|  
|**char**|**Char**|**wchar\_t**|**Char**|  
|**string**|**Chaîne**|**Chaîne**|**Chaîne**|  
|**object**|**Objet**|**Objet**|**Objet**|  
  
 **✓ faire**  utiliser un nom commun, tel que `value` ou `item`, plutôt que de répéter le nom de type, dans les rares cas où un identificateur n’a aucune signification sémantique et le type du paramètre n’est pas important.  
  
## Noms des nouvelles Versions des API existantes  
 **✓ faire** utiliser un nom semblable à l’ancienne API lors de la création de nouvelles versions d’une API existante.  
  
 Cela permet de mettre en évidence la relation entre les API.  
  
 **✓ faire** préférez ajouter un suffixe plutôt qu’un préfixe pour indiquer une nouvelle version d’une API existante.  
  
 Cela permettra de découverte lors de l’exploration de documentation, ou à l’aide d’Intellisense. L’ancienne version de l’API est organisée proche de nouvelles API, car la plupart des navigateurs et Intellisense affichent les identificateurs dans l’ordre alphabétique.  
  
 **✓ envisagez** à l’aide d’un identificateur neuve, mais explicite, au lieu d’ajouter un préfixe ou un suffixe.  
  
 **✓ faire** un suffixe numérique permet d’indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom logique \(par exemple, si elle est une norme industrielle\) et si l’ajout explicite tout suffixe \(ou la modification du nom\) n’est pas une option appropriée.  
  
 **X ne pas** utiliser « Ex » \(ou un texte similaire\) suffixe d’un identificateur pour le distinguer d’une version antérieure de la même API.  
  
 **✓ faire** utilisent le suffixe « 64 » lorsque vous introduisez des versions d’API qui fonctionnent sur un entier 64 bits \(entier long\) au lieu d’un entier 32 bits. Vous devez uniquement suivre cette approche lorsque l’API 32 bits existante existe ; ne le faites pas pour toute nouvelle API avec uniquement une version 64 bits.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)