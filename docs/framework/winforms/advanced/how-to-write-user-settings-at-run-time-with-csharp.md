---
title: "Comment : écrire des paramètres utilisateur au moment de l'exécution avec C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5966aef77c994d2657bd282ad15e8f59a64eeb47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a><span data-ttu-id="b7ae0-102">Comment : écrire des paramètres utilisateur au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="b7ae0-102">How To: Write User Settings at Run Time with C#</span></span> #
<span data-ttu-id="b7ae0-103">Les paramètres de portée application sont en lecture seule et ne peuvent être modifiés qu'au moment du design ou en modifiant le fichier .config entre les sessions d'application.</span><span class="sxs-lookup"><span data-stu-id="b7ae0-103">Settings that are application-scoped are read-only, and can only be changed at design time or by altering the .config file in between application sessions.</span></span> <span data-ttu-id="b7ae0-104">Les paramètres de portée utilisateur peuvent être écrits au moment de l'exécution tout comme vous modifieriez une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="b7ae0-104">Settings that are user-scoped, however, can be written at run time just as you would change any property value.</span></span> <span data-ttu-id="b7ae0-105">La nouvelle valeur est conservée pendant toute la durée de la session d'application.</span><span class="sxs-lookup"><span data-stu-id="b7ae0-105">The new value persists for the duration of the application session.</span></span> <span data-ttu-id="b7ae0-106">Vous pouvez conserver les modifications apportées aux paramètres d'une session d'application à une autre en appelant la méthode Save.</span><span class="sxs-lookup"><span data-stu-id="b7ae0-106">You can persist the changes to the settings between application sessions by calling the Save method.</span></span>  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a><span data-ttu-id="b7ae0-107">Comment : écrire et conserver des paramètres utilisateur au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="b7ae0-107">How To: Write and Persist User Settings at Run Time with C#</span></span>  
  
1.  <span data-ttu-id="b7ae0-108">Accédez au paramètre et attribuez-lui une nouvelle valeur comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="b7ae0-108">Access the setting and assign it a new value as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  <span data-ttu-id="b7ae0-109">Si vous souhaitez conserver les modifications apportées aux paramètres d'une session d'application à l'autre, appelez la méthode Save comme indiqué dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="b7ae0-109">If you want to persist the changes to the settings between application sessions, call the Save method as shown in this example:</span></span>  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     <span data-ttu-id="b7ae0-110">Les paramètres utilisateur sont enregistrés dans un fichier dans un sous-dossier du dossier de données d’application masqué local de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b7ae0-110">User settings are saved in a file within a subfolder of the user’s local hidden application data folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ae0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7ae0-111">See Also</span></span>  
 [<span data-ttu-id="b7ae0-112">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="b7ae0-112">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="b7ae0-113">Guide pratique pour lire des paramètres au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="b7ae0-113">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [<span data-ttu-id="b7ae0-114">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="b7ae0-114">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
