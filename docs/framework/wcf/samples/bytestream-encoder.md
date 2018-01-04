---
title: ByteStream Encoder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de6d5fd64046a72eb6a21b43dd977463f5619850
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bytestream-encoder"></a><span data-ttu-id="feaca-102">ByteStream Encoder</span><span class="sxs-lookup"><span data-stu-id="feaca-102">ByteStream Encoder</span></span>
<span data-ttu-id="feaca-103">Cet exemple montre comment créer un `ByteStreamHttpBinding`, un <xref:System.ServiceModel.Channels.Binding> qui illustre les fonctionnalités de l'encodeur de flux d'octets.</span><span class="sxs-lookup"><span data-stu-id="feaca-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="feaca-104">Discussion</span><span class="sxs-lookup"><span data-stu-id="feaca-104">Discussion</span></span>  
 <span data-ttu-id="feaca-105">Cet exemple montre comment créer un <xref:System.ServiceModel.Channels.Binding> standard à l'aide des éléments de liaison standard <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="feaca-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="feaca-106">Cet exemple montre comment utiliser l'encodeur de flux d'octets pour charger et télécharger une image.</span><span class="sxs-lookup"><span data-stu-id="feaca-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="feaca-107">L'encodeur de flux d'octets ne prend en charge que le transport HTTP et ne prend pas en charge les fonctionnalités telles que la messagerie fiable ou la sécurité.</span><span class="sxs-lookup"><span data-stu-id="feaca-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="feaca-108">Le seul <xref:System.ServiceModel.Channels.MessageVersion> pris en charge est <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="feaca-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="feaca-109">Si vous exécutez cet exemple dans [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] ou [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], veillez à exécuter [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec des privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="feaca-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="feaca-110">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="feaca-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="feaca-111">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="feaca-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="feaca-112">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="feaca-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="feaca-113">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="feaca-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="feaca-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="feaca-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="feaca-115">Ouvrez le fichier ByteStreamHttpBinding.sln dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="feaca-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="feaca-116">Démarrer une nouvelle instance du projet ByteStreamHttpBindingServer en cliquant sur le projet dans l’Explorateur de solutions et en sélectionnant **déboguer**, puis **démarrer une nouvelle instance** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="feaca-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="feaca-117">Démarrer une nouvelle instance du projet ByteStreamHttpBindingClient en cliquant sur le projet dans l’Explorateur de solutions et en sélectionnant **déboguer**, **démarrer une nouvelle instance** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="feaca-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
