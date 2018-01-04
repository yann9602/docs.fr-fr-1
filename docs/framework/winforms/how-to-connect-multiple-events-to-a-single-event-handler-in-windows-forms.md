---
title: "Comment : connecter plusieurs événements à un même gestionnaire d'événements dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfd955b4153c7a2bc54d8b52ff1801541c3a7559
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Comment : connecter plusieurs événements à un même gestionnaire d'événements dans les Windows Forms
Conception de votre application, vous pouvez s’avérer nécessaire d’utiliser un seul gestionnaire d’événements pour plusieurs événements ou d’avoir plusieurs événements à effectuer la même procédure. Par exemple, il est souvent un temps précieux d’avoir une commande de menu à déclencher l’événement de même qu’un bouton sur votre formulaire peut si elles exposent les mêmes fonctionnalités. Cela à l’aide de l’affichage des événements de la fenêtre Propriétés en c# ou à l’aide de la `Handles` (mot clé) et le **nom de la classe** et **nom de la méthode** zones de liste déroulante dans l’éditeur de Code Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Pour connecter plusieurs événements à un seul gestionnaire d’événements en Visual Basic  
  
1.  Avec le bouton droit de la forme et choisissez **afficher le Code**.  
  
2.  À partir de la **nom de la classe** zone de liste déroulante, sélectionnez un des contrôles que vous souhaitez associer le Gestionnaire d’événements.  
  
3.  À partir de la **nom de la méthode** zone de liste déroulante, sélectionnez un des événements que vous souhaitez que le Gestionnaire d’événements.  
  
4.  L’éditeur de Code insère le Gestionnaire d’événements approprié et place le point d’insertion dans la méthode. Dans l’exemple ci-dessous, il est le <xref:System.Windows.Forms.Control.Click> événement pour le <xref:System.Windows.Forms.Button> contrôle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Ajoutez les autres événements vous souhaitez gérés à le `Handles` clause.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Ajoutez le code approprié au gestionnaire d’événements.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Pour connecter plusieurs événements à un seul gestionnaire d’événements en c#  
  
1.  Sélectionnez le contrôle auquel vous souhaitez vous connecter à un gestionnaire d’événements.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le **événements** bouton (![bouton événements](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  Cliquez sur le nom de l’événement que vous souhaitez gérer.  
  
4.  Dans la section de la valeur en regard du nom de l’événement, cliquez sur le bouton de liste déroulante pour afficher la liste des gestionnaires d’événements qui correspondent à la signature de méthode de l’événement que vous souhaitez gérer.  
  
5.  Sélectionnez le Gestionnaire d’événements appropriée dans la liste.  
  
     Code sera ajouté au formulaire pour lier l’événement au gestionnaire d’événements existant.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Vue d'ensemble des gestionnaires d'événements](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
