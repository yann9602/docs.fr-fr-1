---
title: "Objects (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "objects [Visual Basic]"
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique fournit des liens vers d'autres rubriques qui documentent les objets d'exécution Visual Basic et contiennent des tableaux de leurs procédures, propriétés et événements de membre.  
  
## Objets d'exécution Visual Basic  
  
|||  
|-|-|  
|<xref:Microsoft.VisualBasic.Collection>|Offre un moyen pratique pour afficher un groupe connexe d'éléments sous la forme d'un objet unique.|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Contient des informations sur les erreurs d'exécution.|  
|L'objet `My.Application` se compose des classes suivantes :<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> fournit des membres qui sont disponibles dans tous les projets.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> fournit des membres qui sont disponibles dans les applications Windows Forms.<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> fournit des membres qui sont disponibles dans les applications console.|Fournit des données qui sont associées uniquement à l'application ou la DLL actuelle.  Aucune information système ne peut être modifiée à l'aide de `My.Application`.<br /><br /> Certains membres sont uniquement disponibles pour les applications console ou Windows Forms.|  
|`My.Application.Info` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>\)|Fournit des propriétés permettant d'obtenir les informations relatives à une application, telles que le numéro de version, la description, les assemblys chargés, etc.|  
|`My.Application.Log` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>\)|Fournit une propriété et des méthodes pour écrire les informations concernant les événements et exceptions dans les écouteurs de journalisation de l'application.|  
|`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)|Fournit des propriétés permettant de manipuler des composants informatiques, tels que le son, l'horloge, le clavier, le système de fichiers, etc.|  
|`My.Computer.Audio` \(<xref:Microsoft.VisualBasic.Devices.Audio>\)|Fournit des méthodes pour lire des sons.|  
|`My.Computer.Clipboard` \(<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>\)|Fournit des méthodes pour la manipulation du Presse\-papiers.|  
|`My.Computer.Clock` \(<xref:Microsoft.VisualBasic.Devices.Clock>\)|Fournit des propriétés pour accéder à l'heure locale actuelle et au temps UTC \(Universal Coordinated Time\), équivalent à l'heure GMT \(Greenwich Mean Time\), à partir de l'horloge système.|  
|`My.Computer.FileSystem` \(<xref:Microsoft.VisualBasic.FileIO.FileSystem>\)|Fournit des propriétés et des méthodes pour utiliser les lecteurs, les fichiers et les répertoires.|  
|`My.Computer.FileSystem.SpecialDirectories` \(<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>\)|Fournit des propriétés pour accéder aux répertoires communément référencés.|  
|`My.Computer.Info` \(<xref:Microsoft.VisualBasic.Devices.ComputerInfo>\)|Fournit des propriétés pour obtenir des informations concernant la mémoire, les assemblys chargés, le nom et le système d'exploitation de l'ordinateur.|  
|`My.Computer.Keyboard` \(<xref:Microsoft.VisualBasic.Devices.Keyboard>\)|Fournit des propriétés pour accéder à l'état actuel du clavier, par exemple pour savoir quelles touches sont actuellement utilisées, et fournit une méthode pour envoyer des séquences de touches à la fenêtre active.|  
|`My.Computer.Mouse` \(<xref:Microsoft.VisualBasic.Devices.Mouse>\)|Fournit des propriétés permettant d'obtenir des informations relatives au format et à la configuration de la souris qui est installée sur l'ordinateur local.|  
|`My.Computer.Network` \(<xref:Microsoft.VisualBasic.Devices.Network>\)|Fournit une propriété, un événement et des méthodes permettant d'interagir avec le réseau auquel l'ordinateur est connecté.|  
|`My.Computer.Ports` \(<xref:Microsoft.VisualBasic.Devices.Ports>\)|Fournit une propriété et une méthode pour accéder aux ports série de l'ordinateur.|  
|`My.Computer.Registry` \(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>\)|Fournit des propriétés et des méthodes pour manipuler le Registre.|  
|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|Fournit des propriétés permettant d'accéder à une instance de chaque Windows Form déclaré dans le projet actif.|  
|`My.Log` \(<xref:Microsoft.VisualBasic.Logging.AspLog>\)|Fournit une propriété et des méthodes permettant d'écrire des informations sur les événements et les exceptions dans les écouteurs de journalisation des applications Web.|  
|[My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)|Obtient l'objet <xref:System.Web.HttpRequest> pour la page demandée.  L'objet `My.Request` contient des informations sur la demande HTTP actuelle.<br /><br /> L'objet `My.Request` n'est disponible que pour les applications [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].|  
|[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)|Fournit des propriétés et des classes permettant d'accéder aux ressources d'une application.|  
|[My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)|Obtient l'objet <xref:System.Web.HttpResponse> qui est associé à <xref:System.Web.UI.Page>.  Cet objet vous permet d'envoyer des données de réponse HTTP à un client, et contient des informations sur cette réponse.<br /><br /> L'objet `My.Response` n'est disponible que pour les applications [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].|  
|[My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)|Fournit des propriétés et des méthodes permettant d'accéder aux paramètres d'une application.|  
|`My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)|Permet d'accéder aux informations relatives à l'utilisateur actuel.|  
|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|Fournit des propriétés permettant de créer une instance unique de chaque service Web référencé par le projet actif et d'y accéder.|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|Fournit des méthodes et des propriétés pour analyser des fichiers texte structurés.|  
  
## Voir aussi  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../../visual-basic/index.md)