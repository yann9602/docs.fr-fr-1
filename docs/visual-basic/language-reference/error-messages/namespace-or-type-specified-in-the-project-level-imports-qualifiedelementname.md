---
title: "Namespace ou le type spécifié dans les Imports&quot; au niveau du projet&lt;qualifiedelementname&gt;&quot; ne contient aucun membre public ou est introuvable | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
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
ms.openlocfilehash: 5dae6f92f573a57d0974c860500bc7420f55a94f
ms.lasthandoff: 03/13/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace ou le type spécifié dans les Imports' au niveau du projet&lt;qualifiedelementname&gt;' ne contient aucun membre public ou est introuvable
Namespace ou le type spécifié dans les Imports' au niveau du projet\<qualifiedelementname >' ne contient aucun membre public ou est introuvable. Assurez-vous que l’espace de noms ou le type est défini et contient au moins un membre public. Assurez-vous que le nom d’alias ne contient d’autres alias.  
  
 Une propriété Imports d’un projet spécifie un élément conteneur qui ne peut pas être trouvé ou ne définit pas `Public` membres.  
  
 A *contenant l’élément* peut être un espace de noms, classe, structure, module, interface ou énumération. L’élément conteneur contient des membres, tels que des variables, des procédures ou d’autres éléments qui le contient.  
  
 L’objectif de l’importation consiste à permettre à votre code pour accéder aux membres de type ou d’espace de noms sans devoir les qualifier. Votre projet devrez peut-être également ajouter une référence à l’espace de noms ou type. Pour plus d’informations, consultez « Importation d’éléments conteneurs » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Si le compilateur ne peut pas trouver l’élément conteneur spécifié, il ne peut pas résoudre les références qui l’utilisent. S’il trouve l’élément mais l’élément n’expose pas `Public` membres, aucune référence peut être réussie. Dans les deux cas, il n’a aucune signification pour importer l’élément.  
  
 Vous utilisez la **Concepteur de projet** pour spécifier les éléments à importer. Utilisez le **espaces de noms importés** section de la **références** page. Vous pouvez accéder à la **Concepteur de projet** en double-cliquant sur le **mon projet** icône dans **l’Explorateur de solutions**.  
  
 **ID d’erreur :** BC40057  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ouvrez la **Concepteur de projets** et basculez vers le **référence** page.  
  
2.  Dans le **espaces de noms importés** section, vérifiez que l’élément conteneur est accessible à partir de votre projet.  
  
3.  Vérifiez que l’élément conteneur expose au moins un `Public` membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [NIB Comment : modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
