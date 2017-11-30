---
title: "Opérateur GetXmlNamespace (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47ba67bc58debf8f144f6468bf510932414c0698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getxmlnamespace-operator-visual-basic"></a>Opérateur GetXmlNamespace (Visual Basic)
Obtient le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Composants  
 `xmlNamespacePrefix`  
 Facultatif. Chaîne qui identifie le préfixe d’espace de noms XML. Si spécifié, cette chaîne doit être un identificateur XML valide. Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné. Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 Le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML.  
  
## <a name="remarks"></a>Remarques  
 Le `GetXmlNamespace` opérateur Obtient le <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix`.  
  
 Vous pouvez utiliser les préfixes d’espace de noms XML directement dans les littéraux XML et les propriétés d’axe XML. Toutefois, vous devez utiliser le `GetXmlNamespace` pour convertir un préfixe d’espace de noms pour un <xref:System.Xml.Linq.XNamespace> de l’objet avant de pouvoir l’utiliser dans votre code. Vous pouvez ajouter un nom d’élément non qualifié à un <xref:System.Xml.Linq.XNamespace> objet à obtenir un complet <xref:System.Xml.Linq.XName> de l’objet, que de nombreuses [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] méthodes requièrent.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe `ns` comme un préfixe d’espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant qui a le nom qualifié `ns:phone`. Il passe ensuite ce nœud enfant à la `ShowName` sous-routine qui construit un nom qualifié à l’aide de la `GetXmlNamespace` opérateur. Le `ShowName` sous-routine transmet ensuite le nom qualifié à la <xref:System.Xml.Linq.XNode.Ancestors%2A> méthode pour obtenir le parent `ns:contact` nœud.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, il affiche un message qui contient le texte suivant :  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi  
 [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [Accès au code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
