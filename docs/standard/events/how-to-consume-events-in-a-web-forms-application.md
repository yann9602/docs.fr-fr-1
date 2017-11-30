---
title: "Comment : consommer des événements dans une application Web Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="e6671-102">Comment : consommer des événements dans une application Web Forms</span><span class="sxs-lookup"><span data-stu-id="e6671-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="e6671-103">Un scénario courant dans les applications ASP.NET Web Forms consiste à remplir une page Web avec des contrôles, puis effectuer une action spécifique selon le contrôle sur lequel l’utilisateur clique sur.</span><span class="sxs-lookup"><span data-stu-id="e6671-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="e6671-104">Par exemple, un <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> contrôle déclenche un événement lorsque l’utilisateur clique dessus dans la page Web.</span><span class="sxs-lookup"><span data-stu-id="e6671-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="e6671-105">En gérant l’événement, votre application peut exécuter la logique d’application appropriée pour, cliquez sur ce bouton.</span><span class="sxs-lookup"><span data-stu-id="e6671-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="e6671-106">Pour gérer un événement Click du bouton dans une page Web</span><span class="sxs-lookup"><span data-stu-id="e6671-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="e6671-107">Créer une page Web Forms ASP.NET (page Web) qui a un <xref:System.Web.UI.WebControls.Button> contrôler avec la `OnClick` valeur définie sur le nom de la méthode que vous allez définir dans l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="e6671-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="e6671-108">Définir un gestionnaire d’événements qui correspond à la <xref:System.Web.UI.WebControls.Button.Click> signature de délégué d’événement et qui porte le nom que vous avez défini pour le `OnClick` valeur.</span><span class="sxs-lookup"><span data-stu-id="e6671-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="e6671-109">Le <xref:System.Web.UI.WebControls.Button.Click> événement utilise les <xref:System.EventHandler> classe pour le type délégué et la <xref:System.EventArgs> classe pour les données d’événement.</span><span class="sxs-lookup"><span data-stu-id="e6671-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="e6671-110">L’infrastructure de page ASP.NET génère automatiquement le code qui crée une instance de <xref:System.EventHandler> et ajoute cette instance de délégué à la <xref:System.Web.UI.WebControls.Button.Click> l’événement de la <xref:System.Web.UI.WebControls.Button> instance.</span><span class="sxs-lookup"><span data-stu-id="e6671-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="e6671-111">Dans l’événement méthode de gestionnaire que vous avez définie à l’étape 2, ajouter le code pour effectuer les actions qui sont requises lorsque l’événement se produit.</span><span class="sxs-lookup"><span data-stu-id="e6671-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6671-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6671-112">See Also</span></span>  
 [<span data-ttu-id="e6671-113">Événements</span><span class="sxs-lookup"><span data-stu-id="e6671-113">Events</span></span>](../../../docs/standard/events/index.md)
