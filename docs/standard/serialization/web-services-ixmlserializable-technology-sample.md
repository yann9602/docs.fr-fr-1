---
title: IXmlSerializable des services Web, exemple de technologie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72c7e9e1cbf47dd54726a16ddeb58a193d62dc31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a>IXmlSerializable des services Web, exemple de technologie
[Télécharger l’exemple](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 Cet exemple montre comment utiliser <xref:System.Xml.Serialization.IXmlSerializable> pour contrôler la sérialisation de types personnalisés dans les services Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Ouvrez [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et sélectionnez **Nouveau site Web** dans le menu **Fichier**.  
  
2.  Dans le volet gauche de la boîte de dialogue **Nouveau site Web**, sélectionnez le langage de programmation de votre choix, puis dans le volet droit, sélectionnez **Service Web ASP.NET**.  
  
3.  Tapez **IXmlSerializable** comme nom du nouveau service web.  
  
4.  Dans la fenêtre Explorateur de solutions, cliquez avec le bouton droit sur l’icône de Service.asmx et sélectionnez **Supprimer** ; répétez cette étape pour le fichier code-behind Service.asmx.  
  
5.  Cliquez avec le bouton droit sur le répertoire de projet et sélectionnez **Ajouter un élément existant**. Dans la boîte de dialogue, accédez au sous-répertoire Service du répertoire spécifique au langage.  
  
6.  Sélectionnez Service.asmx, puis répétez cette étape pour le fichier code-behind Service.asmx.  
  
7.  Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez au répertoire qui contient le répertoire IXmlSerializable créé à l'étape 3.  
  
8.  Cliquez avec le bouton droit sur l’icône du répertoire IXmlSerializable et sélectionnez **Partage et sécurité**.  
  
9. Sous l’onglet Partage Web, sélectionnez **Partager ce dossier** et vérifiez les paramètres par défaut, dont le nom IXmlSerializable.  
  
10. Cliquez sur **OK**.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une fenêtre de navigateur et sélectionnez sa barre d'adresses.  
  
2.  Tapez **http://localhost/IXmlSerializable/Service.asmx**.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
