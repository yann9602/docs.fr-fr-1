---
title: "Littéral d'instruction de traitement XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a>Littéral d'instruction de traitement XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XProcessingInstruction> objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a>Composants  
 `<?`  
 Obligatoire. Indique le début de l’instruction de traitement XML littéral.  
  
 `piName`  
 Obligatoire. Nom indiquant l’application les cibles d’instruction de traitement. Ne peut pas commencer par « xml » ou « XML ».  
  
 `piData`  
 Facultatif. Chaîne indiquant la manière dont l’application ciblée par `piName` doit traiter le document XML.  
  
 `?>`  
 Obligatoire. Indique la fin de l’instruction de traitement.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XProcessingInstruction>.  
  
## <a name="remarks"></a>Remarques  
 Littéraux d’instruction de traitement XML indiquent la manière dont les applications doivent traiter un document XML. Lorsqu’une application charge un document XML, l’application peut vérifier les instructions de traitement XML pour déterminer comment traiter le document. L’application interprète la signification de `piName` et `piData`.  
  
 Le littéral de document XML utilise la syntaxe est semblable à celle de l’instruction de traitement XML. Pour plus d’informations, consultez [littéral de Document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
> [!NOTE]
>  Le `piName` élément ne peut pas commencer par les chaînes « xml » ou « XML », parce que la spécification XML 1.0 réserve ces identificateurs.  
  
 Vous pouvez assigner un littéral d’instruction de traitement XML à une variable ou l’inclure dans un littéral de document XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes sans avoir besoin de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le littéral d’instruction de traitement XML à un appel à la <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une instruction de traitement identifiant une feuille de style pour un document XML.  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [Littéral de document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
