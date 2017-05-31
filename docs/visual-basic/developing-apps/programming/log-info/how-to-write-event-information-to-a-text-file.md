---
title: "Guide pratique pour écrire des informations sur des événements dans un fichier texte (Visual Basic) │ Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files, writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2701f634332acdfaa81a6bf4e1d1309968366d7f
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a>Comment : écrire des informations sur des événements dans un fichier texte (Visual Basic)
Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application. Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage dans un fichier journal.  
  
### <a name="to-add-and-configure-the-file-log-listener"></a>Pour ajouter et configurer l’écouteur de journalisation du fichier  
  
1.  Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.  
  
     \- ou -  
  
     S’il n’existe pas de fichier app.config :  
  
    1.  Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.  
  
    2.  Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.  
  
    3.  Cliquez sur **Ajouter**.  
  
2.  Recherchez la section `<listeners>` dans le fichier de configuration de l’application.  
  
     Vous pouvez trouver la section \<listeners> dans la section \<source> avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section \<system.diagnostics>, elle-même imbriquée sous la section \<configuration> de plus haut niveau.  
  
3.  Ajoutez cet élément à cette section `<listeners>` :  
  
    ```  
    <add name="FileLogListener" />  
    ```  
  
4.  Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>`, imbriquée dans la section `<configuration>` de plus haut niveau.  
  
5.  Ajoutez cet élément à cette section `<sharedListeners>` :  
  
    ```  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     Remplacez la valeur de l’attribut `customlocation` par le répertoire du journal.  
  
    > [!NOTE]
    >  Pour définir la valeur d’une propriété d’écouteur, utilisez un attribut qui a le même nom que la propriété, en utilisant des minuscules. Par exemple, les attributs `location` et `customlocation` définissent les valeurs des propriétés <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> et <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.  
  
### <a name="to-write-event-information-to-the-file-log"></a>Pour écrire des informations sur les événements dans le journal du fichier  
  
-   Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal du fichier. Pour plus d’informations, consultez [Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).  
  
     Une fois l’écouteur de journalisation du fichier configuré pour un assembly, il reçoit tous les messages écrits par `My.Application.Log` à partir de cet assembly.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [Guide pratique : enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
