---
title: "Enregistrements de suivi personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51c47c3b11c912c1c67fe0d9ed4960de42f8a852
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tracking-records"></a>Enregistrements de suivi personnalisé
Cette rubrique montre comment créer des enregistrements de suivi personnalisés et les remplir avec des données à émettre avec les enregistrements.  
  
## <a name="emitting-custom-tracking-records"></a>Émission d'enregistrements de suivi personnalisé  
 Les enregistrements de suivi personnalisés peuvent être issus d'une activité de code comme indiqué dans l'exemple suivant.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 Un <xref:System.Activities.Tracking.CustomTrackingRecord> est émis dans une activité de code en appelant la méthode <xref:System.Activities.NativeActivityContext.Track%2A> sur `ActvityContext`.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Analyse des Applications avec AppFabric](http://go.microsoft.com/fwlink/?LinkId=201275)
