---
title: "Imports Statement (XML Namespace) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ImportsXmlns"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML namespace [Visual Basic], importing"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "namespaces [Visual Basic], importing"
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports Statement (XML Namespace)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Importe des préfixes d'espace de noms XML à utiliser dans les littéraux et propriétés d'axe XML.  
  
## Syntaxe  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## Composants  
 `xmlNamespacePrefix`  
 Facultatif.  Chaîne par laquelle les éléments et les attributs XML peuvent faire référence à `xmlNamespaceName`.  Si aucun `xmlNamespacePrefix` n'est fourni, l'espace de noms XML importé est celui par défaut.  Doit être un identificateur XML valide.  Pour plus d'informations, consultez [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Obligatoire.  Chaîne identifiant l'espace de noms XML qui est importé.  
  
## Notes  
 Vous pouvez utiliser l'instruction `Imports` pour définir des espaces de noms XML globaux utilisables avec les littéraux XML et les propriétés d'axe XML, ou comme paramètres passés à l'opérateur `GetXmlNamespace`.  \(Pour plus d'informations sur l'utilisation de l'instruction `Imports` pour importer un alias utilisable lorsque des noms de type sont utilisés dans votre code, consultez [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).\) La syntaxe de déclaration d'un espace de noms XML à l'aide de l'instruction `Imports` est identique à celle utilisée en XML.  Par conséquent, vous pouvez copier une déclaration d'espace de noms d'un fichier XML et l'utiliser dans une instruction `Imports`.  
  
 Les préfixes d'espace de noms XML sont utiles lorsque vous souhaitez créer à plusieurs reprises des éléments XML issus du même espace de noms.  Le préfixe d'espace de noms XML déclaré avec l'instruction `Imports` est global en ce sens qu'il est à disposition de l'ensemble du code du fichier.  Vous pouvez l'utiliser pour créer des littéraux d'élément XML et accéder aux propriétés d'axe XML.  Pour plus d'informations, consultez [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Si vous définissez un espace de noms XML global sans préfixe d'espace de noms \(par exemple, `Imports <xmlns="http://SomeNameSpace>"`\), il est considéré comme l'espace de noms XML par défaut.  L'espace de noms XML par défaut est utilisé pour tout littéral d'élément XML ou propriété d'axe d'attribut XML qui ne spécifie pas explicitement d'espace de noms.  L'espace de noms par défaut est également utilisé si l'espace de noms spécifié est l'espace de noms vide \(autrement dit, `xmlns=""`\).  L'espace de noms XML par défaut ne s'applique pas aux attributs XML des littéraux XML ou aux propriétés d'axe d'attribut XML qui n'ont pas d'espace de noms.  
  
 Les espaces de noms XML définis dans un littéral XML, appelés *espaces de noms XML locaux*, sont prioritaires sur les espaces de noms XML définis par l'instruction `Imports` comme globaux.  Les espaces de noms XML définis par l'instruction `Imports` sont prioritaires sur les espaces de noms XML importés pour un projet Visual Basic.  Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s'applique pas aux expressions incorporées.  
  
 Les espaces de noms XML globaux suivent les mêmes règles de portée et de définition que les espaces de noms .NET Framework.  En conséquence, vous pouvez inclure une instruction `Imports` pour définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework.  Cela inclut les fichiers de code et les espaces de noms importés au niveau du projet.  Pour plus d'informations sur les espaces de noms importés au niveau du projet, consultez [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  
  
 Chaque fichier source peut contenir un nombre quelconque d'instructions `Imports`.  Ces derniers doivent respecter les déclarations d'option, telles que l'instruction `Option Strict`, et doivent précéder les déclarations d'élément de programmation, telles que les instructions `Module` ou `Class`.  
  
## Exemple  
 L'exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`.  Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
```  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## Exemple  
 L'exemple suivant importe le préfixe d'espace de noms XML `ns`.  Il crée alors un littéral XML qui utilise le préfixe d'espace de noms et affiche le formulaire final de l'élément.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Notez que le compilateur a converti le préfixe d'espace de noms XML en définition de préfixe locale à partir d'un préfixe global.  
  
## Exemple  
 L'exemple suivant importe le préfixe d'espace de noms XML `ns`.  Il utilise alors le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Patrick Hines`  
  
## Voir aussi  
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)   
 [GetXmlNamespace Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)