---
title: "Cette application à instance unique n’a pas pu se connecter à l’instance d’origine | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17a3ecd69e0e0974b2a8fc50090097b93dc0def3
ms.lasthandoff: 03/13/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>Impossible de connecter cette application à instance unique à l’instance d’origine
Impossible de connecter cette application à instance unique à l'instance d'origine. Ce problème peut avoir les causes suivantes :  
  
-   L'instance d'origine a cessé de répondre.  
  
-   L'application n'a pas l'autorisation de créer des objets du noyau. Pour plus d’informations sur les objets du noyau, consultez [mutex](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).  
  
     Le nom de base des objets du noyau est une concaténation entre le GUID de l'assembly, le numéro de la version principale et le numéro de la version secondaire. Le nom de base pourrait être, par exemple, `3639f15d-9547-43da-8145-60da347829915.1`.  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>Pour corriger cette erreur lors du développement d’une application  
  
1.  Vérifiez que l’application continue de répondre.  
  
2.  Vérifiez que l’application dispose d’autorisations suffisantes pour créer des objets noyaux.  
  
3.  Redémarrez l’instance d’origine de l’application.  
  
4.  Redémarrez l’ordinateur pour annuler tout processus susceptible d’utiliser la ressource permettant de se connecter à l’application de l’instance d’origine.  
  
5.  Notez les circonstances dans lesquelles l’erreur s’est produite, puis contactez les services de support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [NIB : Comment : spécifier le comportement d’instanciation pour une Application (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Principes de base du débogueur](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)   
 [PAVEOVER du support technique et accessibilité](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
