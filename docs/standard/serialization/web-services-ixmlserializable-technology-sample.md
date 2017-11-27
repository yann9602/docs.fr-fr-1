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
# <a name="web-services-ixmlserializable-technology-sample"></a><span data-ttu-id="11ba7-102">IXmlSerializable des services Web, exemple de technologie</span><span class="sxs-lookup"><span data-stu-id="11ba7-102">Web Services IXmlSerializable Technology Sample</span></span>
[<span data-ttu-id="11ba7-103">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="11ba7-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 <span data-ttu-id="11ba7-104">Cet exemple montre comment utiliser <xref:System.Xml.Serialization.IXmlSerializable> pour contrôler la sérialisation de types personnalisés dans les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="11ba7-104">This sample shows how to use <xref:System.Xml.Serialization.IXmlSerializable> to control the serialization of custom types in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="11ba7-105">Pour générer l'exemple à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="11ba7-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="11ba7-106">Ouvrez [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] et sélectionnez **Nouveau site Web** dans le menu **Fichier**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-106">Open [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="11ba7-107">Dans le volet gauche de la boîte de dialogue **Nouveau site Web**, sélectionnez le langage de programmation de votre choix, puis dans le volet droit, sélectionnez **Service Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-107">In the left pane of the **New Web Site** dialog, select your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="11ba7-108">Tapez **IXmlSerializable** comme nom du nouveau service web.</span><span class="sxs-lookup"><span data-stu-id="11ba7-108">Type **IXmlSerializable** as the name of the new Web service.</span></span>  
  
4.  <span data-ttu-id="11ba7-109">Dans la fenêtre Explorateur de solutions, cliquez avec le bouton droit sur l’icône de Service.asmx et sélectionnez **Supprimer** ; répétez cette étape pour le fichier code-behind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="11ba7-109">In the Solution Explorer window, right-click the icon for Service.asmx and select **Delete**; repeat this step for the Service.asmx codebehind file.</span></span>  
  
5.  <span data-ttu-id="11ba7-110">Cliquez avec le bouton droit sur le répertoire de projet et sélectionnez **Ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-110">Right-click the project directory and select **Add Existing Item**.</span></span> <span data-ttu-id="11ba7-111">Dans la boîte de dialogue, accédez au sous-répertoire Service du répertoire spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="11ba7-111">In the dialog, navigate to the Service subdirectory of the language-specific directory.</span></span>  
  
6.  <span data-ttu-id="11ba7-112">Sélectionnez Service.asmx, puis répétez cette étape pour le fichier code-behind Service.asmx.</span><span class="sxs-lookup"><span data-stu-id="11ba7-112">Select Service.asmx, then repeat this step for the Service.asmx codebehind file.</span></span>  
  
7.  <span data-ttu-id="11ba7-113">Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez au répertoire qui contient le répertoire IXmlSerializable créé à l'étape 3.</span><span class="sxs-lookup"><span data-stu-id="11ba7-113">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the directory that contains IXmlSerializable directory that you created in step 3 above.</span></span>  
  
8.  <span data-ttu-id="11ba7-114">Cliquez avec le bouton droit sur l’icône du répertoire IXmlSerializable et sélectionnez **Partage et sécurité**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-114">Right-click the icon for the IXmlSerializable directory and select **Sharing and Security**.</span></span>  
  
9. <span data-ttu-id="11ba7-115">Sous l’onglet Partage Web, sélectionnez **Partager ce dossier** et vérifiez les paramètres par défaut, dont le nom IXmlSerializable.</span><span class="sxs-lookup"><span data-stu-id="11ba7-115">In the Web Sharing tab, select **Share this Folder**, and confirm the default settings, including the name IXmlSerializable.</span></span>  
  
10. <span data-ttu-id="11ba7-116">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-116">Click **OK**.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="11ba7-117">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="11ba7-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="11ba7-118">Ouvrez une fenêtre de navigateur et sélectionnez sa barre d'adresses.</span><span class="sxs-lookup"><span data-stu-id="11ba7-118">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="11ba7-119">Tapez **http://localhost/IXmlSerializable/Service.asmx**.</span><span class="sxs-lookup"><span data-stu-id="11ba7-119">Type **http://localhost/IXmlSerializable/Service.asmx**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ba7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11ba7-120">See Also</span></span>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
