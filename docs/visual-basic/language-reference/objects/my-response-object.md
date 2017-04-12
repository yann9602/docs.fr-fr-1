---
title: My.Response, objet | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWebExtension.Response
- My.Response
dev_langs:
- VB
helpviewer_keywords:
- My.Response object
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: e2ae9a659bb7575023dfa1847c9d405d0f7d6ac3
ms.lasthandoff: 03/13/2017

---
# <a name="myresponse-object"></a>My.Response, objet
Obtient l' <xref:System.Web.HttpResponse>objet associé à le <xref:System.Web.UI.Page>.</xref:System.Web.UI.Page> </xref:System.Web.HttpResponse> Cet objet vous permet d’envoyer des données de réponse HTTP à un client et contient des informations sur cette réponse.  
  
## <a name="remarks"></a>Remarques  
 Le `My.Response` objet contient actuel <xref:System.Web.HttpResponse>objet associé à la page.</xref:System.Web.HttpResponse>  
  
 Le `My.Response` objet n’est disponible pour [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] les applications.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant obtient la collection d’en-têtes à partir de la `My.Request` et utilise le `My.Response` objet à écrire dans la page ASP.NET.  
  
 [!code-vb[VbVbalrMyWeb n °&1;](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Web.HttpResponse></xref:System.Web.HttpResponse>   
 [My.Request (objet)](../../../visual-basic/language-reference/objects/my-request-object.md)
