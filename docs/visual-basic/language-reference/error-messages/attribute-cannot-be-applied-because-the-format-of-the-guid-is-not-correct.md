---
title: "«&lt;attribut&gt;&quot; ne peut pas être appliquée car le format du GUID &quot;&lt;nombre&gt;&quot; n’est pas correct | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
dev_langs:
- VB
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
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
ms.openlocfilehash: f22f9ecd63582e2a346702919cf9154819b8eb0e
ms.lasthandoff: 03/13/2017

---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>«&lt;attribut&gt;' ne peut pas être appliquée car le format du GUID '&lt;nombre&gt;' n’est pas correct
Un `COMClassAttribute` bloc d’attributs Spécifie un identificateur global unique (GUID) qui n’est pas conforme au format correct. `COMClassAttribute`utilise les GUID pour identifier de façon unique la classe, l’interface et l’événement de création.  
  
 Un GUID se compose de 16 octets, dont les huit premiers sont numériques et les huit derniers sont binaires. Il est généré par les utilitaires Microsoft, tels que uuidgen.exe et est garanti pour être unique dans l’espace et de temps.  
  
 **ID d’erreur :** BC32500  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Déterminez le GUID ou le GUID nécessaire pour identifier l’objet COM approprié.  
  
2.  Vérifiez que les chaînes de GUID présentées au bloc d’attributs `COMClassAttribute` sont copiées correctement.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Guid></xref:System.Guid>   
[Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)


