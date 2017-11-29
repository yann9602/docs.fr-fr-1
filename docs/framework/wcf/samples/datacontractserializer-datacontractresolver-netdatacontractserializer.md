---
title: "Utilisation de DataContractSerializer et DataContractResolver pour fournir les fonctionnalités de NetDataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d189b68cc8321dace0418a3c1e4b1b3c21cfd3ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="a88a1-102">Utilisation de DataContractSerializer et DataContractResolver pour fournir les fonctionnalités de NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="a88a1-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="a88a1-103">Cet exemple montre comment l'utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> avec un <xref:System.Runtime.Serialization.DataContractResolver> approprié fournit les mêmes fonctionnalités que <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a88a1-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="a88a1-104">Cet exemple montre comment créer le <xref:System.Runtime.Serialization.DataContractResolver> approprié et comment l'ajouter au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a88a1-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a88a1-105">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="a88a1-105">Sample details</span></span>  
 <span data-ttu-id="a88a1-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> diffère de <xref:System.Runtime.Serialization.DataContractSerializer> sur un point important : <xref:System.Runtime.Serialization.NetDataContractSerializer> inclut des informations de type CLR dans le XML sérialisé ; <xref:System.Runtime.Serialization.DataContractSerializer> ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="a88a1-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="a88a1-107">Par conséquent, <xref:System.Runtime.Serialization.NetDataContractSerializer> peut être utilisé uniquement si les extrémités de sérialisation et de désérialisation partagent toutes deux les mêmes types CLR.</span><span class="sxs-lookup"><span data-stu-id="a88a1-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="a88a1-108">Toutefois, il est recommandé d'utiliser <xref:System.Runtime.Serialization.DataContractSerializer>, car il offre de meilleures performances que <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a88a1-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="a88a1-109">Vous pouvez modifier les informations sérialisées dans <xref:System.Runtime.Serialization.DataContractSerializer> en lui ajoutant un <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="a88a1-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>  
  
 <span data-ttu-id="a88a1-110">Cet exemple est composé de deux projets.</span><span class="sxs-lookup"><span data-stu-id="a88a1-110">This sample consists of two projects.</span></span> <span data-ttu-id="a88a1-111">Le premier projet utilise <xref:System.Runtime.Serialization.NetDataContractSerializer> pour sérialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="a88a1-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="a88a1-112">Le second projet utilise <xref:System.Runtime.Serialization.DataContractSerializer> avec un <xref:System.Runtime.Serialization.DataContractResolver> pour fournir les mêmes fonctionnalités que le premier projet.</span><span class="sxs-lookup"><span data-stu-id="a88a1-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>  
  
 <span data-ttu-id="a88a1-113">L'exemple de code suivant illustre l'implémentation d'un <xref:System.Runtime.Serialization.DataContractResolver> personnalisé, nommé `MyDataContractResolver`, qui est ajouté au <xref:System.Runtime.Serialization.DataContractSerializer> du projet DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="a88a1-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private XmlDictionary dictionary = new XmlDictionary();  
  
    public MyDataContractResolver()  
    {  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        if (type == null)  
        {  
            type = Type.GetType(typeName + ", " + typeNamespace);  
        }  
        return type;  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
        if (typeName == null || typeNamespace == null)  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add(dataContractType.FullName);  
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);  
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a88a1-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="a88a1-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a88a1-115">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="a88a1-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a88a1-116">Cliquez sur le fichier solution et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a88a1-116">Right-click the solution file and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="a88a1-117">Dans le **les Pages de propriétés de Solution** boîte de dialogue, sous **propriétés communes**, **projet de démarrage**, sélectionnez **plusieurs projets de démarrage :**.</span><span class="sxs-lookup"><span data-stu-id="a88a1-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>  
  
4.  <span data-ttu-id="a88a1-118">À côté du **DCSwithDCR** projet, sélectionnez **Démarrer** à partir de la **Action** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a88a1-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>  
  
5.  <span data-ttu-id="a88a1-119">À côté du **NetDCS** projet, sélectionnez **Démarrer** à partir de la **Action** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="a88a1-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>  
  
6.  <span data-ttu-id="a88a1-120">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a88a1-120">Click **OK** to close the dialog.</span></span>  
  
7.  <span data-ttu-id="a88a1-121">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="a88a1-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
8.  <span data-ttu-id="a88a1-122">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="a88a1-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a88a1-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a88a1-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a88a1-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a88a1-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a88a1-125">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a88a1-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a88a1-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a88a1-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a><span data-ttu-id="a88a1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a88a1-127">See Also</span></span>
