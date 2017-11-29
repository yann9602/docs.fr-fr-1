---
title: "Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6410ef93a706c047047aa24b3d47f8915e928015
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
