---
title: "Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- asynchronous calls
- Web services, accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: 14
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f191ccb5f42f9cfc5dc4e44e58d2338422207aa1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)
Cet exemple attache un gestionnaire à l'événement de gestionnaire asynchrone d'un service web pour qu'il puisse récupérer le résultat d'un appel de méthode asynchrone. Cet exemple utilise le service web DemoTemperatureService disponible à l’adresse http://www.xmethods.net.  
  
 Quand vous faites référence à un service web dans votre projet dans l'IDE (Integrated Development Environment) de [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], il est ajouté à l'objet `My.WebServices` et l'IDE génère une classe proxy cliente pour accéder à un service web spécifié.  
  
 La classe proxy vous permet d'appeler les méthodes du service web de manière synchrone (votre application attend que la fonction soit terminée). De plus, le proxy crée des membres supplémentaires pour aider à appeler la méthode de manière asynchrone. Pour chaque fonction du service web, *NameOfWebServiceFunction*, le proxy crée une sous-routine *NameOfWebServiceFunction*`Async`, un événement *NameOfWebServiceFunction*`Completed` et une classe *NameOfWebServiceFunction*`CompletedEventArgs`. Cet exemple montre comment utiliser les membres asynchrones pour accéder à la fonction `getTemp` du service web DemoTemperatureService.  
  
> [!NOTE]
>  Ce code ne fonctionne pas dans les applications web, car ASP.NET ne prend pas en charge l'objet `My.WebServices`.  
  
### <a name="to-call-a-web-service-asynchronously"></a>Pour appeler un service web de manière asynchrone  
  
1.  Référencez le service web DemoTemperatureService disponible à l’adresse http://www.xmethods.net. L'adresse est  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  Ajoutez un gestionnaire d'événements pour l'événement `getTempCompleted` :  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  Vous ne pouvez pas utiliser l'instruction `Handles` pour associer un gestionnaire d'événements aux événements de l'objet `My.WebServices`.  
  
3.  Ajoutez un champ pour suivre si le gestionnaire d'événements a été ajouté à l'événement `getTempCompleted` :  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  Ajoutez une méthode pour ajouter le gestionnaire d'événements à l'événement `getTempCompleted`, si nécessaire, et pour appeler la méthode `getTempAsynch` :  
  
    ```  
    Sub CallGetTempAsync(ByVal zipCode As Integer)  
        If Not handlerAttached Then  
            AddHandler My.WebServices.  
                TemperatureService.getTempCompleted,   
                AddressOf Me.TS_getTempCompleted  
            handlerAttached = True  
        End If  
        My.WebServices.TemperatureService.getTempAsync(zipCode)  
    End Sub  
    ```  
  
     Pour appeler la méthode web `getTemp` de manière asynchrone, appelez la méthode `CallGetTempAsync`. Quand la méthode web se termine, sa valeur de retour est passée au gestionnaire d'événements `getTempCompletedHandler`.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux services web d’une application](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)   
 [My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md)

