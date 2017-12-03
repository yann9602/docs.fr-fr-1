---
title: DataContractResolver
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aefe0bc0e0be17c2585499e4c943b43672907dfc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="datacontractresolver"></a><span data-ttu-id="900cc-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="900cc-102">DataContractResolver</span></span>
<span data-ttu-id="900cc-103">Cet exemple montre comment les processus de sérialisation et de désérialisation peuvent être personnalisés à l'aide de la classe <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="900cc-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="900cc-104">Cet exemple illustre comment utiliser DataContractResolver pour mapper les types CLR vers et depuis une représentation xsi:type pendant la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="900cc-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="900cc-105">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="900cc-105">Sample Details</span></span>  
 <span data-ttu-id="900cc-106">L'exemple définit les types CLR suivants.</span><span class="sxs-lookup"><span data-stu-id="900cc-106">The sample defines the following CLR types.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
  
namespace Types  
{  
    [DataContract]  
    public class Customer  
    {  
        [DataMember]  
        public string Name { get; set; }  
    }  
  
    [DataContract]  
    public class VIPCustomer : Customer  
    {  
        [DataMember]  
        public string VipInfo { get; set; }  
    }  
  
    [DataContract]  
    public class RegularCustomer : Customer  
    {  
    }  
  
    [DataContract]  
    public class PreferredVIPCustomer : VIPCustomer  
    {  
    }  
}  
```  
  
 <span data-ttu-id="900cc-107">L'exemple charge l'assembly, extrait chacun de ces types, puis les sérialise et les désérialise.</span><span class="sxs-lookup"><span data-stu-id="900cc-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="900cc-108">Le <xref:System.Runtime.Serialization.DataContractResolver> est intégré au processus de sérialisation en passant une instance de la classe dérivée de <xref:System.Runtime.Serialization.DataContractResolver> au constructeur <xref:System.Runtime.Serialization.DataContractSerializer>, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="900cc-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>  
  
```csharp  
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));  
```  
  
 <span data-ttu-id="900cc-109">Dans l'exemple, les types CLR sont ensuite sérialisés comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="900cc-109">The sample then serializes the CLR types as shown in the following code example.</span></span>  
  
```csharp  
Assembly assembly = Assembly.Load(new AssemblyName("Types"));  
  
public void serialize(Type type)  
{  
    Object instance = Activator.CreateInstance(type);  
  
    Console.WriteLine("----------------------------------------");  
    Console.WriteLine();  
    Console.WriteLine("Serializing type: {0}", type.Name);  
    Console.WriteLine();  
    this.buffer = new StringBuilder();  
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))  
    {  
        try  
        {  
            this.serializer.WriteObject(xmlWriter, instance);  
        }  
        catch (SerializationException error)  
        {  
            Console.WriteLine(error.ToString());  
        }  
    }  
    Console.WriteLine(this.buffer.ToString());  
}  
```  
  
 <span data-ttu-id="900cc-110">Les xsi:types sont ensuite désérialisés comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="900cc-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>  
  
```csharp  
public void deserialize(Type type)  
{  
    Console.WriteLine();  
    Console.WriteLine("Deserializing type: {0}", type.Name);  
    Console.WriteLine();  
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))  
    {  
        Object obj = this.serializer.ReadObject(xmlReader);  
    }  
}  
```  
  
 <span data-ttu-id="900cc-111">Puisque le <xref:System.Runtime.Serialization.DataContractResolver> personnalisé est passé au constructeur <xref:System.Runtime.Serialization.DataContractSerializer>, le <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> est appelé pendant la sérialisation pour mapper un type CLR à un `xsi:type` équivalent.</span><span class="sxs-lookup"><span data-stu-id="900cc-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="900cc-112">De même, le <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> est appelé pendant la désérialisation pour mapper le `xsi:type` à un type CLR équivalent.</span><span class="sxs-lookup"><span data-stu-id="900cc-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="900cc-113">Dans cet exemple, le <xref:System.Runtime.Serialization.DataContractResolver> est défini comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="900cc-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>  
  
 <span data-ttu-id="900cc-114">L'exemple de code suivant est une classe dérivée de <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="900cc-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();  
    Assembly assembly;  
  
    public MyDataContractResolver(Assembly assembly)  
    {  
        this.assembly = assembly;  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        XmlDictionaryString tName;  
        XmlDictionaryString tNamespace;  
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))  
        {  
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);  
        }  
        else  
        {  
            return null;  
        }  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        string name = dataContractType.Name;  
        string namesp = dataContractType.Namespace;  
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);   
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);  
        if (!dictionary.ContainsKey(dataContractType.Name))  
        {  
            dictionary.Add(name, typeName);  
        }  
        if (!dictionary.ContainsKey(dataContractType.Namespace))  
        {  
            dictionary.Add(namesp, typeNamespace);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="900cc-115">Dans le cadre de l'exemple, le projet Types génère l'assembly avec tous les types utilisés dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="900cc-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="900cc-116">Utilisez ce projet pour ajouter, supprimer ou modifier les types qui seront sérialisés.</span><span class="sxs-lookup"><span data-stu-id="900cc-116">Use this project to add, remove or modify the types that will be serialized.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="900cc-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="900cc-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="900cc-118">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier solution DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="900cc-118">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="900cc-119">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="900cc-119">To run the solution, press F5</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="900cc-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="900cc-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="900cc-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="900cc-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="900cc-122">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="900cc-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="900cc-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="900cc-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="900cc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="900cc-124">See Also</span></span>  
 [<span data-ttu-id="900cc-125">À l’aide d’un programme de résolution de contrat de données</span><span class="sxs-lookup"><span data-stu-id="900cc-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
