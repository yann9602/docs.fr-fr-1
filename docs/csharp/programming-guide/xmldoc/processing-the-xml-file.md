---
title: "Traitement du fichier XML (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML (C#), traiter"
  - "traitement XML (C#)"
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# Traitement du fichier XML (Guide de programmation C#)
Le compilateur génère une chaîne d'identification pour chaque construction de votre code qui est placée entre balises de manière à générer de la documentation.  \(Pour plus d'informations sur l'ajout de balises à votre code, consultez [Balises recommandées pour commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md).\) La chaîne d'identification identifie de manière unique la construction.  Les programmes qui traitent le fichier XML peuvent utiliser la chaîne d'identification pour identifier l'élément de métadonnées\/réflexion du .NET Framework correspondant auquel s'applique la documentation.  
  
 Le fichier XML n'est pas une représentation hiérarchique de votre code, mais une simple liste comportant un identificateur généré pour chaque élément.  
  
 Lorsqu'il génère les chaînes d'identification, le compilateur respecte les règles suivantes :  
  
-   La chaîne ne doit contenir aucun espace.  
  
-   La première partie de la chaîne d'identification identifie le type de membre à l'aide d'un caractère unique suivi de deux\-points.  Les types de membres suivants sont utilisés :  
  
    |Caractère|Description|  
    |---------------|-----------------|  
    |N|Espace de noms<br /><br /> Vous ne pouvez pas ajouter de commentaires de documentation à un espace de noms, mais vous pouvez ajouter des références cref à ces commentaires, lorsqu'elles sont prises en charge.|  
    |T|type : classe, interface, struct, enum, délégué|  
    |F|champ|  
    |P|propriété \(y compris les indexeurs ou autres propriétés indexées\)|  
    |M|méthode \(y compris des méthodes spéciales telles que les constructeurs, les opérateurs, etc.\)|  
    |E|event|  
    |\!|chaîne d'erreur<br /><br /> Le reste de la chaîne fournit des informations sur l'erreur.  Le compilateur C\# génère des informations sur l'erreur pour les liens impossibles à résoudre.|  
  
-   La deuxième partie de la chaîne est composée du nom complet de l'élément, à partir de la racine de l'espace de noms.  Le nom de l'élément, ses types englobants et l'espace de noms sont séparés par des points.  Si le nom de l'élément lui\-même comporte des points, ils sont remplacés par un dièse \('\#'\).  Par principe, aucun nom d'élément ne doit contenir de signe dièse à l'origine.  Par exemple, le nom complet du constructeur String est "System.String.\#ctor".  
  
-   Pour les propriétés et méthodes, s'il existe des arguments pour la méthode, la liste des arguments figure à la suite entre parenthèses.  En l'absence d'arguments, aucune parenthèse n'est mentionnée.  Les arguments sont séparés par des virgules.  L'encodage de chaque argument correspond directement à son encodage dans une signature .NET Framework :  
  
    -   Types de base.  Les types réguliers \(ELEMENT\_TYPE\_CLASS ou ELEMENT\_TYPE\_VALUETYPE\) sont représentés par le nom complet du type.  
  
    -   Types intrinsèques \(par exemple, ELEMENT\_TYPE\_I4, ELEMENT\_TYPE\_OBJECT, ELEMENT\_TYPE\_STRING, ELEMENT\_TYPE\_TYPEDBYREF.  et ELEMENT\_TYPE\_VOID\) sont représentés comme le nom qualifié complet du type correspondant.  Exemple : System.Int32 ou System.TypedReference.  
  
    -   ELEMENT\_TYPE\_PTR est représenté par un '\*' à la suite du type modifié.  
  
    -   ELEMENT\_TYPE\_BYREF est représenté par un '@' à la suite du type modifié.  
  
    -   ELEMENT\_TYPE\_PINNED est représenté par un '^' à la suite du type modifié.  Le compilateur C\# ne génère jamais ceci.  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ est représenté par un '&#124;' et le nom complet de la classe de modificateur, à la suite du type modifié.  Le compilateur C\# ne génère jamais ceci.  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT est représenté par un '\!' et le nom complet de la classe de modificateur, à la suite du type modifié.  
  
    -   ELEMENT\_TYPE\_SZARRAY est représenté par "\[\]" à la suite du type d'élément du tableau.  
  
    -   ELEMENT\_TYPE\_GENERICARRAY est représenté par "\[?\]" à la suite du type d'élément du tableau.  Le compilateur C\# ne génère jamais ceci.  
  
    -   ELEMENT\_TYPE\_ARRAY est représenté par \[*limite\_inférieure*:`size`,*limite\_inférieure*:`size`\], où le nombre de virgules correspond au rang \- 1, et les limite inférieure et taille de chaque dimension, lorsqu'elles sont connues, sont représentées sous forme décimale.  Lorsqu'une limite inférieure ou une taille n'est pas spécifiée, elle est seulement omise.  Si la limite inférieure et la taille d'une dimension particulière sont omises, le signe ':' est également omis.  Par exemple, un tableau à 2 dimensions avec des limites inférieures égales à 1, mais sans tailles spécifiées est représenté par \[1:,1:\].  
  
    -   ELEMENT\_TYPE\_FNPTR est représenté sous la forme "\=FUNC:`type`\(*signature*\)", où `type` est le type de retour et *signature* l'argument de la méthode.  En l'absence d'arguments, les parenthèses sont omises.  Le compilateur C\# ne génère jamais ceci.  
  
     Les composants de signature suivants ne sont pas représentés parce qu'ils ne sont jamais utilisés pour différencier les méthodes surchargées :  
  
    -   convention d'appel  
  
    -   type de retour  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   Uniquement pour les opérateurs de conversion \(op\_Implicit et op\_Explicit\), la valeur de retour de la méthode est encodée sous la forme d'un '~' suivi du type de retour, conformément à l'encodage effectué plus haut.  
  
-   Pour les types génériques, le nom du type sera suivi du caractère \` puis d'un nombre qui indique le nombre de paramètres de type générique.  Par exemple :  
  
     `<member name="T:SampleClass`2">` est la balise d'un type défini comme `public class SampleClass<T, U>`.  
  
     Pour les méthodes qui prennent des types génériques comme paramètres, les paramètres de type générique sont spécifiés comme des nombres précédés de caractères \` \(par exemple \`0, \`1\).  Chaque nombre représente une notation de tableau de base zéro pour les paramètres génériques du type.  
  
## Exemples  
 Les exemples ci\-dessous illustrent la manière dont les chaînes d'identification doivent être générées pour une classe et ses membres :  
  
 [!code-cs[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#21)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires de documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)