---
title: "XML Processing Instruction Literal (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralProcessingInstruction"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML literals [Visual Basic], processing instruction"
  - "XML processing instruction literal [Visual Basic]"
  - "processing instruction literal [Visual Basic]"
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Processing Instruction Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Littéral représentant un objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## Syntaxe  
  
```  
<?piName [ = piData ] ?>  
```  
  
## Composants  
 `<?`  
 Obligatoire.  Dénote le démarrage du littéral d'instruction de traitement XML.  
  
 `piName`  
 Obligatoire.  Nom indiquant l'application ciblée par l'instruction de traitement.  Ne peut commencer par "xml" ni "XML".  
  
 `piData`  
 Facultatif.  Chaîne indiquant la manière dont l'application ciblée par `piName` doit traiter le document XML.  
  
 `?>`  
 Obligatoire.  Dénote la fin de l'instruction de traitement.  
  
## Valeur de retour  
 Objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## Notes  
 Les littéraux d'instruction de traitement XML indiquent la manière dont les applications doivent traiter un document XML.  Lorsqu'une application charge un document XML, elle peut vérifier les instructions de traitement XML pour déterminer comment traiter le document.  L'application interprète la signification de `piName` et `piData`.  
  
 Le littéral de document XML utilise une syntaxe semblable à celle de l'instruction de traitement XML.  Pour plus d'informations, consultez [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  L'élément `piName` ne peut pas commencer par les chaînes « xml » ou « XML », parce que la spécification XML 1.0 réserve ces identificateurs.  
  
 Vous pouvez assigner un littéral d'instruction de traitement XML à une variable ou l'inclure dans un littéral de document XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes, sans devoir utiliser de caractères de continuation de ligne.  Cela vous permet de copier le contenu d'un document XML et de le coller directement dans un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] convertit le littéral d'instruction de traitement XML en un appel au constructeur <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>.  
  
## Exemple  
 L'exemple suivant crée une instruction de traitement qui identifie une feuille de style pour un document XML.  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XProcessingInstruction>   
 [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)