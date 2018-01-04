---
title: "Comment : modifier la valeur d'un paramètre entre des sessions d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c00e61001d9c8877b1fcaa0e938c92249c7915e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>Comment : modifier la valeur d'un paramètre entre des sessions d'application
Dans certains cas, vous pouvez modifier la valeur d’un paramètre entre des sessions d’application une fois que l’application a été compilée et déployée. Par exemple, vous pouvez modifier une chaîne de connexion pour pointer vers l’emplacement de la base de données correcte. Étant donné que les outils de conception ne sont pas disponibles une fois que l’application a été compilée et déployée, vous devez modifier la valeur du paramètre manuellement dans le fichier.  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>Pour modifier la valeur d’un paramètre entre des Sessions d’Application  
  
1.  À l’aide de Microsoft Notepad ou un autre texte ou éditeur XML, ouvrez le fichier .config associé à votre application.  
  
2.  Recherchez l’entrée pour le paramètre que vous souhaitez modifier. Il doit ressembler à l’exemple présenté ci-dessous.  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  Tapez une nouvelle valeur pour votre paramètre et enregistrez le fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de paramètres d'application et de paramètres utilisateur](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [Vue d'ensemble des paramètres d'application](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
