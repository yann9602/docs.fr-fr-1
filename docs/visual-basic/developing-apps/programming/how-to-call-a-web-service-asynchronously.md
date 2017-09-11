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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="a6ae5-102">Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6ae5-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>
<span data-ttu-id="a6ae5-103">Cet exemple attache un gestionnaire à l'événement de gestionnaire asynchrone d'un service web pour qu'il puisse récupérer le résultat d'un appel de méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="a6ae5-104">Cet exemple utilise le service web DemoTemperatureService disponible à l’adresse http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-104">This example used the DemoTemperatureService Web service at http://www.xmethods.net.</span></span>  
  
 <span data-ttu-id="a6ae5-105">Quand vous faites référence à un service web dans votre projet dans l'IDE (Integrated Development Environment) de [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], il est ajouté à l'objet `My.WebServices` et l'IDE génère une classe proxy cliente pour accéder à un service web spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-105">When you reference a Web service in your project in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>  
  
 <span data-ttu-id="a6ae5-106">La classe proxy vous permet d'appeler les méthodes du service web de manière synchrone (votre application attend que la fonction soit terminée).</span><span class="sxs-lookup"><span data-stu-id="a6ae5-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="a6ae5-107">De plus, le proxy crée des membres supplémentaires pour aider à appeler la méthode de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="a6ae5-108">Pour chaque fonction du service web, *NameOfWebServiceFunction*, le proxy crée une sous-routine *NameOfWebServiceFunction*`Async`, un événement *NameOfWebServiceFunction*`Completed` et une classe *NameOfWebServiceFunction*`CompletedEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="a6ae5-109">Cet exemple montre comment utiliser les membres asynchrones pour accéder à la fonction `getTemp` du service web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6ae5-110">Ce code ne fonctionne pas dans les applications web, car ASP.NET ne prend pas en charge l'objet `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>  
  
### <a name="to-call-a-web-service-asynchronously"></a><span data-ttu-id="a6ae5-111">Pour appeler un service web de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="a6ae5-111">To call a Web service asynchronously</span></span>  
  
1.  <span data-ttu-id="a6ae5-112">Référencez le service web DemoTemperatureService disponible à l’adresse http://www.xmethods.net.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-112">Reference the DemoTemperatureService Web service at http://www.xmethods.net.</span></span> <span data-ttu-id="a6ae5-113">L'adresse est</span><span class="sxs-lookup"><span data-stu-id="a6ae5-113">The address is</span></span>  
  
    ```  
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl  
    ```  
  
2.  <span data-ttu-id="a6ae5-114">Ajoutez un gestionnaire d'événements pour l'événement `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="a6ae5-114">Add an event handler for the `getTempCompleted` event:</span></span>  
  
    ```  
    Private Sub getTempCompletedHandler(ByVal sender As Object,   
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)  
  
        MsgBox("Temperature: " & e.Result)  
    End Sub  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="a6ae5-115">Vous ne pouvez pas utiliser l'instruction `Handles` pour associer un gestionnaire d'événements aux événements de l'objet `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>  
  
3.  <span data-ttu-id="a6ae5-116">Ajoutez un champ pour suivre si le gestionnaire d'événements a été ajouté à l'événement `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="a6ae5-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>  
  
    ```  
    Private handlerAttached As Boolean = False  
    ```  
  
4.  <span data-ttu-id="a6ae5-117">Ajoutez une méthode pour ajouter le gestionnaire d'événements à l'événement `getTempCompleted`, si nécessaire, et pour appeler la méthode `getTempAsynch` :</span><span class="sxs-lookup"><span data-stu-id="a6ae5-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsynch` method:</span></span>  
  
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
  
     <span data-ttu-id="a6ae5-118">Pour appeler la méthode web `getTemp` de manière asynchrone, appelez la méthode `CallGetTempAsync`.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="a6ae5-119">Quand la méthode web se termine, sa valeur de retour est passée au gestionnaire d'événements `getTempCompletedHandler`.</span><span class="sxs-lookup"><span data-stu-id="a6ae5-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ae5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6ae5-120">See Also</span></span>  
 <span data-ttu-id="a6ae5-121">[Accès aux services web d’une application](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md) </span><span class="sxs-lookup"><span data-stu-id="a6ae5-121">[Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md) </span></span>  
 [<span data-ttu-id="a6ae5-122">My.WebServices (objet)</span><span class="sxs-lookup"><span data-stu-id="a6ae5-122">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)

