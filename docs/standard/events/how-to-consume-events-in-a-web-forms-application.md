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
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Comment : consommer des événements dans une application Web Forms
Un scénario courant dans les applications ASP.NET Web Forms consiste à remplir une page Web avec des contrôles, puis effectuer une action spécifique selon le contrôle sur lequel l’utilisateur clique sur. Par exemple, un <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> contrôle déclenche un événement lorsque l’utilisateur clique dessus dans la page Web. En gérant l’événement, votre application peut exécuter la logique d’application appropriée pour, cliquez sur ce bouton.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Pour gérer un événement Click du bouton dans une page Web  
  
1.  Créer une page Web Forms ASP.NET (page Web) qui a un <xref:System.Web.UI.WebControls.Button> contrôler avec la `OnClick` valeur définie sur le nom de la méthode que vous allez définir dans l’étape suivante.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Définir un gestionnaire d’événements qui correspond à la <xref:System.Web.UI.WebControls.Button.Click> signature de délégué d’événement et qui porte le nom que vous avez défini pour le `OnClick` valeur.  
  
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
  
     Le <xref:System.Web.UI.WebControls.Button.Click> événement utilise les <xref:System.EventHandler> classe pour le type délégué et la <xref:System.EventArgs> classe pour les données d’événement. L’infrastructure de page ASP.NET génère automatiquement le code qui crée une instance de <xref:System.EventHandler> et ajoute cette instance de délégué à la <xref:System.Web.UI.WebControls.Button.Click> l’événement de la <xref:System.Web.UI.WebControls.Button> instance.  
  
3.  Dans l’événement méthode de gestionnaire que vous avez définie à l’étape 2, ajouter le code pour effectuer les actions qui sont requises lorsque l’événement se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../docs/standard/events/index.md)
