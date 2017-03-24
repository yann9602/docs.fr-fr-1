---
title: "GetXmlNamespace, opérateur (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
dev_langs:
- VB
helpviewer_keywords:
- GetXmlNamespace operator
- GetXmlNamespace keyword
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 929ba4edae9e155245228670424a3898896da807
ms.lasthandoff: 03/13/2017

---
# <a name="getxmlnamespace-operator-visual-basic"></a>Opérateur GetXmlNamespace (Visual Basic)
Obtient le <xref:System.Xml.Linq.XNamespace>objet qui correspond au préfixe d’espace de noms XML spécifié.</xref:System.Xml.Linq.XNamespace>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Composants  
 `xmlNamespacePrefix`  
 Facultatif. Chaîne qui identifie le préfixe d’espace de noms XML. Si fourni, cette chaîne doit être un identificateur XML valide. Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné. Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 Le <xref:System.Xml.Linq.XNamespace>objet qui correspond au préfixe d’espace de noms XML.</xref:System.Xml.Linq.XNamespace>  
  
## <a name="remarks"></a>Remarques  
 Le `GetXmlNamespace` opérateur Obtient le <xref:System.Xml.Linq.XNamespace>objet qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix`.</xref:System.Xml.Linq.XNamespace>  
  
 Vous pouvez utiliser les préfixes d’espace de noms XML directement dans les littéraux XML et les propriétés d’axe XML. Toutefois, vous devez utiliser le `GetXmlNamespace` pour convertir un préfixe d’espace de noms pour un <xref:System.Xml.Linq.XNamespace>de l’objet avant que vous pouvez l’utiliser dans votre code.</xref:System.Xml.Linq.XNamespace> Vous pouvez ajouter un nom d’élément non qualifié à un <xref:System.Xml.Linq.XNamespace>objet pour obtenir un complet <xref:System.Xml.Linq.XName>de l’objet, que de nombreuses [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] méthodes nécessitent.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe `ns` comme un préfixe d’espace de noms XML. Il utilise ensuite le préfixe d’espace de noms pour créer un littéral XML et accéder au premier nœud enfant qui a le nom qualifié `ns:phone`. Il passe alors ce nœud enfant à la `ShowName` sous-routine qui construit un nom qualifié à l’aide de la `GetXmlNamespace` (opérateur). Le `ShowName` sous-routine passe ensuite le nom qualifié à la <xref:System.Xml.Linq.XNode.Ancestors%2A>méthode pour obtenir le parent `ns:contact` nœud.</xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
 [!code-vb[VbXMLSamples&#38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, il affiche un message qui contient le texte suivant :  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi  
 [Imports, instruction (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Accès au code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
