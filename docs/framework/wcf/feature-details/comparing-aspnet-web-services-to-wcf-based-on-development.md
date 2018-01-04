---
title: "Comparaison des services Web ASP.NET et de WCF du point de vue du développement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c12bd11cee62cd769f7dffc142806fa5ab1b0137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="cbb24-102">Comparaison des services Web ASP.NET et de WCF du point de vue du développement</span><span class="sxs-lookup"><span data-stu-id="cbb24-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="cbb24-103"> a une option de mode de compatibilité ASP.NET pour permettre la programmation et la configuration d'applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comme services Web ASP.NET, et reproduire leur comportement.</span><span class="sxs-lookup"><span data-stu-id="cbb24-103"> has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="cbb24-104">Les sections suivantes proposent une comparaison entre les services Web ASP.NET et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en évoquant les exigences requises pour développer des applications qui utilisent ces deux technologies.</span><span class="sxs-lookup"><span data-stu-id="cbb24-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="cbb24-105">Représentation des données</span><span class="sxs-lookup"><span data-stu-id="cbb24-105">Data Representation</span></span>  
 <span data-ttu-id="cbb24-106">Le développement d'un service Web avec ASP.NET commence en général par la définition de tous les types de données complexes que le service doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="cbb24-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="cbb24-107">ASP.NET repose sur le <xref:System.Xml.Serialization.XmlSerializer> pour traduire en XML des données représentées par les types .NET Framework pour la transmission en direction ou depuis un service et pour traduire des données reçues comme XML en objets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbb24-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="cbb24-108">La définition des types de données complexes à utiliser par un service ASP.NET nécessite de définir les classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser depuis le XML ou vers celui-ci.</span><span class="sxs-lookup"><span data-stu-id="cbb24-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="cbb24-109">Ces classes peuvent être écrites manuellement ou générées à partir des définitions des types dans le schéma XML à l'aide de l'utilitaire de prise en charge des types de données/schémas XML de ligne de commande, xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="cbb24-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="cbb24-110">Les éléments suivants répertorient les problèmes clés à connaître lors de la définition des classes .NET Framework que le <xref:System.Xml.Serialization.XmlSerializer> peut sérialiser en XML ou depuis celui-ci :</span><span class="sxs-lookup"><span data-stu-id="cbb24-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="cbb24-111">Seuls les champs et les propriétés publics des objets .NET Framework sont traduits en XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="cbb24-112">Les instances de classes de collection peuvent être sérialisées en XML uniquement si les classes implémentent l'interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="cbb24-113">Les classes qui implémentent l'interface <xref:System.Collections.IDictionary>, telles que <xref:System.Collections.Hashtable>, ne peuvent pas être sérialisées en XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="cbb24-114">Le grand nombre de types d'attributs dans l'espace de noms <xref:System.Xml.Serialization> peut être ajouté à une classe .NET Framework et à ses membres pour contrôler le mode de représentation en XML des instances de la classe.</span><span class="sxs-lookup"><span data-stu-id="cbb24-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="cbb24-115">Le développement d'applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] commence aussi généralement par la définition de types complexes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-115">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="cbb24-116">Il est possible de configurer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour qu'il utilise les mêmes types .NET Framework que les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="cbb24-117">Le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> peuvent être ajoutés aux types .NET Framework pour indiquer que les instances du type doivent être sérialisées en XML, et quels champs ou propriétés particuliers du type doivent être sérialisés, comme indiqué dans l’exemple suivant code.</span><span class="sxs-lookup"><span data-stu-id="cbb24-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
//Example One:   
[DataContract]  
public class LineItem  
{  
    [DataMember]  
    public string ItemNumber;  
    [DataMember]  
    public decimal Quantity;  
    [DataMember]  
    public decimal UnitPrice;  
}  
  
//Example Two:   
public class LineItem  
{  
    [DataMember]  
    private string itemNumber;  
    [DataMember]  
    private decimal quantity;  
    [DataMember]  
    private decimal unitPrice;  
  
    public string ItemNumber  
    {  
      get  
      {  
          return this.itemNumber;  
      }  
  
      set  
      {  
          this.itemNumber = value;  
      }  
    }  
  
    public decimal Quantity  
    {  
        get  
        {  
            return this.quantity;  
        }  
  
        set  
        {  
            this.quantity = value;  
        }  
    }  
  
    public decimal UnitPrice  
    {  
      get  
      {  
          return this.unitPrice;  
      }  
  
      set  
      {  
          this.unitPrice = value;  
      }  
    }  
}  
  
//Example Three:   
public class LineItem  
{  
     private string itemNumber;  
     private decimal quantity;  
     private decimal unitPrice;  
  
     [DataMember]  
     public string ItemNumber  
     {  
       get  
       {  
          return this.itemNumber;  
       }  
  
       set  
       {  
           this.itemNumber = value;  
       }  
     }  
  
     [DataMember]  
     public decimal Quantity  
     {  
          get  
          {  
              return this.quantity;  
          }  
  
          set  
          {  
             this.quantity = value;  
          }  
     }  
  
     [DataMember]  
     public decimal UnitPrice  
     {  
          get  
          {  
              return this.unitPrice;  
          }  
  
          set  
          {  
              this.unitPrice = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="cbb24-118"><xref:System.Runtime.Serialization.DataContractAttribute> signifie que zéro ou plusieurs des champs ou des propriétés d'un type vont être sérialisés, alors que <xref:System.Runtime.Serialization.DataMemberAttribute> indique qu'une propriété ou un champ particulier va être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="cbb24-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="cbb24-119"><xref:System.Runtime.Serialization.DataContractAttribute> peut être appliqué à une classe ou à une structure.</span><span class="sxs-lookup"><span data-stu-id="cbb24-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="cbb24-120">Le <xref:System.Runtime.Serialization.DataMemberAttribute> peut être appliqué à un champ ou à une propriété, et les champs et les propriétés auxquels l'attribut est appliqué peuvent être publics ou privés.</span><span class="sxs-lookup"><span data-stu-id="cbb24-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="cbb24-121">Les instances des types auxquelles sont appliquées le <xref:System.Runtime.Serialization.DataContractAttribute> sont appelées des contrats de données dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="cbb24-122">Elles sont sérialisées en XML à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="cbb24-123">Les éléments suivants répertorient une liste des différences principales entre l'utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> et celle de <xref:System.Xml.Serialization.XmlSerializer> et les divers attributs de l'espace de noms <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="cbb24-124">Le <xref:System.Xml.Serialization.XmlSerializer> et les attributs de l'espace de noms <xref:System.Xml.Serialization> sont conçus pour vous permettre de mapper des types .NET Framework à des types valides définis dans le schéma XML, ils fournissent ainsi un contrôle très précis sur la manière de représenter un type en XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="cbb24-125">Les <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> fournissent très peu de contrôle sur la manière de représenter un type en XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="cbb24-126">Vous pouvez spécifier uniquement les espaces de noms et les noms utilisés pour représenter le type et ses champs ou propriétés dans le XML, et la séquence dans laquelle les champs et propriétés apparaissent dans le XML :</span><span class="sxs-lookup"><span data-stu-id="cbb24-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
    [DataContract(  
    Namespace="urn:Contoso:2006:January:29",  
    Name="LineItem")]  
    public class LineItem  
    {  
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]  
         public string itemNumber;  
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]  
         public decimal quantity;  
         [DataMember(Name="Price",IsRequired=false,Order = 2)]  
         public decimal unitPrice;  
    }  
    ```  
  
     <span data-ttu-id="cbb24-127">Tout ce qui concerne la structure du XML utilisé pour représenter le type .NET est déterminé par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="cbb24-128">En ne permettant qu'un contrôle limité sur la manière de représenter un type en XML, le processus de sérialisation devient très prévisible pour le <xref:System.Runtime.Serialization.DataContractSerializer>, et, par conséquent, plus facile à optimiser.</span><span class="sxs-lookup"><span data-stu-id="cbb24-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="cbb24-129">Un avantage pratique de la conception de <xref:System.Runtime.Serialization.DataContractSerializer> est d'offrir de meilleures performances, une amélioration d'environ dix pour cent.</span><span class="sxs-lookup"><span data-stu-id="cbb24-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="cbb24-130">Les attributs à utiliser avec le <xref:System.Xml.Serialization.XmlSerializer> n'indiquent pas quels champs ou propriétés du type sont sérialisés en XML, alors que le <xref:System.Runtime.Serialization.DataMemberAttribute> à utiliser avec le <xref:System.Runtime.Serialization.DataContractSerializer> indique explicitement les champs ou les propriétés sérialisées.</span><span class="sxs-lookup"><span data-stu-id="cbb24-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="cbb24-131">Par conséquent, les contrats de données sont des contrats explicites sur la structure des données qu'une application doit envoyer et recevoir.</span><span class="sxs-lookup"><span data-stu-id="cbb24-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="cbb24-132">Le <xref:System.Xml.Serialization.XmlSerializer> peut traduire uniquement les membres publics d'un objet .NET en XML, le <xref:System.Runtime.Serialization.DataContractSerializer> peut traduire les membres des objets en XML indépendamment des modificateurs d'accès de ces membres.</span><span class="sxs-lookup"><span data-stu-id="cbb24-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="cbb24-133">Étant donné qu'il peut sérialiser en XML les membres non publics des types, le <xref:System.Runtime.Serialization.DataContractSerializer> offre moins de restrictions sur la variété des types .NET qu'il peut sérialiser en XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="cbb24-134">En particulier, il peut traduire en XML des types tels que <xref:System.Collections.Hashtable> qui implémentent l'interface <xref:System.Collections.IDictionary>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="cbb24-135">Il est plus probable que <xref:System.Runtime.Serialization.DataContractSerializer> puisse sérialiser les instances d'un type .NET préexistant en XML sans avoir à modifier la définition du type ou à développer un wrapper qui lui sera destiné.</span><span class="sxs-lookup"><span data-stu-id="cbb24-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="cbb24-136">Une autre conséquence de la capacité de <xref:System.Runtime.Serialization.DataContractSerializer> d'accéder aux membres non publics d'un type est qu'il requiert une confiance totale, ce qui n'est pas le cas de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="cbb24-137">L'autorisation d'accès au code de confiance totale permet un accès complet à toutes les ressources sur un ordinateur qui sont accessibles à l'aide des informations d'identification dans le cadre desquelles le code s'exécute.</span><span class="sxs-lookup"><span data-stu-id="cbb24-137">The Full Trust code access permission give complete access to all resources on a machine that can be access using the credentials under which the code is executing.</span></span> <span data-ttu-id="cbb24-138">Ces options doivent être utilisées avec prudence dans la mesure où du code d'un niveau de confiance suffisant accède à toutes les ressources de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cbb24-138">This options should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="cbb24-139">Le <xref:System.Runtime.Serialization.DataContractSerializer> incorpore une prise en charge du suivi des versions :</span><span class="sxs-lookup"><span data-stu-id="cbb24-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="cbb24-140">Le <xref:System.Runtime.Serialization.DataMemberAttribute> a une propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> qui peut prendre une valeur false pour les membres ajoutés aux nouvelles versions d'un contrat de données qui ne figuraient pas dans les versions antérieures, ce qui permet aux applications avec la version plus récente du contrat de traiter des versions antérieures.</span><span class="sxs-lookup"><span data-stu-id="cbb24-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="cbb24-141">En implémentant l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> par le contrat de données, il est possible pour le <xref:System.Runtime.Serialization.DataContractSerializer> de passer des membres définis dans des versions plus récentes d'un contrat de données par l'intermédiaire d'applications avec des versions antérieures du contrat.</span><span class="sxs-lookup"><span data-stu-id="cbb24-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="cbb24-142">En dépit de toutes ces différences, le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="cbb24-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="cbb24-143">La classe suivante, qui a des attributs utilisables avec les deux sérialiseurs, est traduite dans un XML à la sémantique identique par le <xref:System.Xml.Serialization.XmlSerializer> et par le <xref:System.Runtime.Serialization.DataContractAttribute> :</span><span class="sxs-lookup"><span data-stu-id="cbb24-143">The following class, which has attributes for use with both of the serializers, are translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
[Serializable]  
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]  
[DataContract(Namespace="urn:Contoso:2006:January:29")]  
public class LineItem  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
```  
  
 <span data-ttu-id="cbb24-144">Kit de développement logiciel (SDK) Windows inclut un outil de ligne de commande appelé le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Comme l’outil xsd.exe utilisé avec les services Web ASP.NET, Svcutil.exe peut générer des définitions des types de données .NET à partir du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="cbb24-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="cbb24-145">Les types sont des contrats de données si le <xref:System.Runtime.Serialization.DataContractSerializer> peut émettre du XML au format défini par le schéma XML ; sinon, ils sont destinés à être sérialisés à l'aide du <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-145">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="cbb24-146">L'outil, Svcutil.exe, peut aussi générer le schéma XML à partir des contrats de données qui utilisent son commutateur `/dataContractOnly`.</span><span class="sxs-lookup"><span data-stu-id="cbb24-146">The tool, Svcutil.exe, can also be made to generate XML Schema from data contracts using its `/dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbb24-147">Bien que les services ASP.NET Web utilisent le <xref:System.Xml.Serialization.XmlSerializer>, et que le mode de compatibilité ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fait reproduire aux services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] le comportement des services Web ASP.NET, l'option de compatibilité ASP.NET n'oblige pas à faire appel à <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-147">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="cbb24-148">Il est toujours possible d'utiliser le <xref:System.Runtime.Serialization.DataContractSerializer> avec des services qui s'exécutent en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-148">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="cbb24-149">Développement des services</span><span class="sxs-lookup"><span data-stu-id="cbb24-149">Service Development</span></span>  
 <span data-ttu-id="cbb24-150">Pour développer un service à l'aide d'ASP.NET, il est d'usage d'ajouter l'attribut <xref:System.Web.Services.WebService> à une classe, et le <xref:System.Web.Services.WebMethodAttribute> à une des méthodes de cette classe qui servent d'opérations du service :</span><span class="sxs-lookup"><span data-stu-id="cbb24-150">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
[WebService]  
public class Service : T:System.Web.Services.WebService  
{  
    [WebMethod]  
    public string Echo(string input)   
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="cbb24-151">ASP.NET 2.0 introduit la possibilité d'ajouter l'attribut <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> à une interface plutôt qu'à une classe, et d'écrire une classe pour implémenter l'interface :</span><span class="sxs-lookup"><span data-stu-id="cbb24-151">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="cbb24-152">L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> représente un contrat pour les opérations effectuées par le service qui peuvent être réutilisées avec différentes classes qui implémentent éventuellement ce même contrat de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="cbb24-152">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="cbb24-153">Un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est fourni en définissant un ou plusieurs points de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="cbb24-154">Un point de terminaison est défini par une adresse, une liaison et un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-154">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="cbb24-155">L'adresse définit l'emplacement du service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-155">The address defines where the service is located.</span></span> <span data-ttu-id="cbb24-156">La liaison spécifie le mode de communication avec le service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-156">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="cbb24-157">Le contrat de service définit les opérations que le service peut effectuer.</span><span class="sxs-lookup"><span data-stu-id="cbb24-157">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="cbb24-158">Le contrat de service est défini habituellement en premier en ajoutant <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> à une interface :</span><span class="sxs-lookup"><span data-stu-id="cbb24-158">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="cbb24-159">Le <xref:System.ServiceModel.ServiceContractAttribute> spécifie que l'interface définit un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], et le <xref:System.ServiceModel.OperationContractAttribute> indique laquelle des méthodes (le cas échéant) de l'interface définit les opérations du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-159">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="cbb24-160">Une fois qu'un contrat de service a été défini, il est implémenté dans une classe, en implémentant par la classe l'interface qui définit le contrat de service :</span><span class="sxs-lookup"><span data-stu-id="cbb24-160">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="cbb24-161">Une classe qui implémente un contrat de service est connue sous le nom d'un type de service dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-161">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="cbb24-162">L'étape suivante consiste à associer une adresse et une liaison à un type de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-162">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="cbb24-163">Cette opération s'effectue généralement dans un fichier de configuration, soit en modifiant le fichier directement, soit à l'aide d'un éditeur de configurations fourni avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-163">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="cbb24-164">Voici un exemple d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cbb24-164">Here is an example of a configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
     <system.serviceModel>  
      <services>  
      <service name="Service ">  
       <endpoint   
        address="EchoService"  
        binding="basicHttpBinding"  
        contract="IEchoService "/>  
      </service>  
      </services>  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="cbb24-165">La liaison spécifie le jeu de protocoles permettant de communiquer avec l'application.</span><span class="sxs-lookup"><span data-stu-id="cbb24-165">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="cbb24-166">Le tableau suivant répertorie les liaisons fournies par le système qui représentent des options courantes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-166">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="cbb24-167">Nom</span><span class="sxs-lookup"><span data-stu-id="cbb24-167">Name</span></span>|<span data-ttu-id="cbb24-168">Objectif</span><span class="sxs-lookup"><span data-stu-id="cbb24-168">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="cbb24-169">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-169">BasicHttpBinding</span></span>|<span data-ttu-id="cbb24-170">Interopérabilité avec les services et les clients Web qui prennent en charge WS-BasicProfile 1.1 et Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="cbb24-170">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="cbb24-171">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-171">WSHttpBinding</span></span>|<span data-ttu-id="cbb24-172">Interopérabilité avec les services et clients Web qui prennent en charge les protocoles WS-* sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="cbb24-172">Interoperability with Web services and clients that support the WS-* protocols over HTTP.</span></span>|  
|<span data-ttu-id="cbb24-173">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-173">WSDualHttpBinding</span></span>|<span data-ttu-id="cbb24-174">Communication HTTP en duplex au cours de laquelle le récepteur d'un message initial ne répond pas directement à l'expéditeur initial, mais peut transmettre pendant un certain temps un nombre illimité de réponses à l'aide de HTTP conformément aux protocoles WS-*.</span><span class="sxs-lookup"><span data-stu-id="cbb24-174">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-* protocols.</span></span>|  
|<span data-ttu-id="cbb24-175">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-175">WSFederationBinding</span></span>|<span data-ttu-id="cbb24-176">Communication HTTP au cours de laquelle l'accès aux ressources d'un service peut être contrôlé en fonction des informations d'identification émises par un fournisseur d'informations d'identification identifié explicitement.</span><span class="sxs-lookup"><span data-stu-id="cbb24-176">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="cbb24-177">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-177">NetTcpBinding</span></span>|<span data-ttu-id="cbb24-178">Communication sécurisée, fiable, hautes performances entre des entités logicielles [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="cbb24-178">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="cbb24-179">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-179">NetNamedPipeBinding</span></span>|<span data-ttu-id="cbb24-180">Communication sécurisée, fiable, hautes performances entre des entités logicielles [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cbb24-180">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="cbb24-181">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-181">NetMsmqBinding</span></span>|<span data-ttu-id="cbb24-182">Communication entre des entités logicielles [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cbb24-182">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="cbb24-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-183">MsmqIntegrationBinding</span></span>|<span data-ttu-id="cbb24-184">Communication entre une entité logicielle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et une autre entité logicielle à l'aide de MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cbb24-184">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="cbb24-185">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="cbb24-185">NetPeerTcpBinding</span></span>|<span data-ttu-id="cbb24-186">Communication entre des entités logicielles [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide de réseaux homologues Windows.</span><span class="sxs-lookup"><span data-stu-id="cbb24-186">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="cbb24-187">La liaison fournie par le système, <xref:System.ServiceModel.BasicHttpBinding>, incorpore le jeu de protocoles pris en charge par les services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-187">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="cbb24-188">Les liaisons personnalisées pour les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont définies facilement comme des collections de classes d'élément de liaison utilisées par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour implémenter des protocoles individuels.</span><span class="sxs-lookup"><span data-stu-id="cbb24-188">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="cbb24-189">Les nouveaux éléments de liaison peuvent être écrits pour représenter des protocoles supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cbb24-189">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="cbb24-190">Le comportement interne des types de service peut être ajusté à l'aide des propriétés d'une famille de classes appelées des comportements.</span><span class="sxs-lookup"><span data-stu-id="cbb24-190">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="cbb24-191">Dans ce contexte, la classe <xref:System.ServiceModel.ServiceBehaviorAttribute> est utilisée pour spécifier que le type de service doit être multithread.</span><span class="sxs-lookup"><span data-stu-id="cbb24-191">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="cbb24-192">Certains comportements, comme <xref:System.ServiceModel.ServiceBehaviorAttribute>, sont des attributs.</span><span class="sxs-lookup"><span data-stu-id="cbb24-192">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="cbb24-193">Ceux dont les propriétés peuvent être définies par les administrateurs, peuvent être modifiés dans la configuration d'une application.</span><span class="sxs-lookup"><span data-stu-id="cbb24-193">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="cbb24-194">Pour programmer des types de service, la classe <xref:System.ServiceModel.OperationContext> est fréquemment utilisée.</span><span class="sxs-lookup"><span data-stu-id="cbb24-194">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="cbb24-195">Sa propriété statique <xref:System.ServiceModel.OperationContext.Current%2A> fournit l'accès aux informations du contexte d'exécution d'une opération.</span><span class="sxs-lookup"><span data-stu-id="cbb24-195">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="cbb24-196"><xref:System.ServiceModel.OperationContext> est semblable aux classes <xref:System.Web.HttpContext> et <xref:System.EnterpriseServices.ContextUtil>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-196"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="cbb24-197">Hébergement</span><span class="sxs-lookup"><span data-stu-id="cbb24-197">Hosting</span></span>  
 <span data-ttu-id="cbb24-198">Les services Web ASP.NET sont compilés dans un assembly de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-198">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="cbb24-199">Un fichier appelé le fichier de service est fourni avec l'extension .asmx et contient une directive `@ WebService` qui identifie la classe qui contient le code pour le service et l'assembly qui la contient.</span><span class="sxs-lookup"><span data-stu-id="cbb24-199">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="cbb24-200">Le fichier de service est copié dans une racine d'application ASP.NET dans les services IIS (Internet Information Services), et l'assembly est copié dans le sous-répertoire \bin de cette racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="cbb24-200">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="cbb24-201">L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="cbb24-201">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 <span data-ttu-id="cbb24-202">Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être hébergés facilement dans les services IIS 5.1 ou 6.0, le service WAS (Windows Process Activation Service) fourni dans le cadre des services IIS 7.0, et dans toutes les applications .NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-202">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="cbb24-203">Pour héberger un service dans les services IIS 5.1 ou 6.0, le service doit utiliser HTTP comme protocole de transport de communications.</span><span class="sxs-lookup"><span data-stu-id="cbb24-203">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="cbb24-204">Pour héberger un service dans les services IIS 5.1, 6.0 ou dans le service WAS, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="cbb24-204">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="cbb24-205">Compilez le type de service dans un assembly de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-205">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="cbb24-206">Créez un fichier de service avec une extension .svc et une directive `@ ServiceHost` pour identifier le type de service :</span><span class="sxs-lookup"><span data-stu-id="cbb24-206">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="cbb24-207">Copiez le fichier de service dans un répertoire virtuel, et l'assembly dans le sous-répertoire \bin de ce répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="cbb24-207">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="cbb24-208">Copiez le fichier de configuration dans le répertoire virtuel et nommez-le Web.config.</span><span class="sxs-lookup"><span data-stu-id="cbb24-208">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="cbb24-209">L'application est ensuite accessible depuis l'URL du fichier de service dans la racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="cbb24-209">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="cbb24-210">Pour héberger un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une application .NET, compilez le type de service dans un assembly de bibliothèque de classes référencé par l'application et programmez l'application pour héberger le service à l'aide de la classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-210">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="cbb24-211">Les éléments suivants sont un exemple de la programmation de base requise :</span><span class="sxs-lookup"><span data-stu-id="cbb24-211">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="cbb24-212">Cet exemple indique comment les adresses pour un ou plusieurs protocoles de transport sont spécifiées dans la construction d'un <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-212">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="cbb24-213">Ces adresses sont connues sous le nom d'adresses de base.</span><span class="sxs-lookup"><span data-stu-id="cbb24-213">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="cbb24-214">L'adresse fournie pour un point de terminaison d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est une adresse relative à une adresse de base de l'hôte du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cbb24-214">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="cbb24-215">L'hôte peut avoir une adresse de base pour chaque protocole de transport de communication.</span><span class="sxs-lookup"><span data-stu-id="cbb24-215">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="cbb24-216">Dans l'exemple de configuration du fichier de configuration précédent, l'objet <xref:System.ServiceModel.BasicHttpBinding> sélectionné comme point de terminaison fait appel à HTTP comme protocole de transport, l'adresse du point de terminaison, `EchoService`, est donc relative à l'adresse de base HTTP de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="cbb24-216">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="cbb24-217">Dans le cas de l'hôte de l'exemple précédent, l'adresse de base HTTP est http://www.contoso.com:8000/.</span><span class="sxs-lookup"><span data-stu-id="cbb24-217">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="cbb24-218">Pour un service hébergé dans les services IIS ou WAS, l'adresse de base est l'URL du fichier de service du service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-218">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="cbb24-219">Seuls les services hébergé dans les services IIS ou WAS, et configurés exclusivement avec HTTP comme protocole de transport, peuvent utiliser l'option de mode de compatibilité ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-219">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="cbb24-220">L'activation de cette option requiert les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-220">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="cbb24-221">Le programmeur doit ajouter l'attribut <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> au type de service et spécifier que le mode de compatibilité ASP.NET est autorisé ou requis.</span><span class="sxs-lookup"><span data-stu-id="cbb24-221">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="cbb24-222">L'administrateur doit configurer l'application pour qu'elle utilise le mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-222">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
    ```xml  
    <configuration>  
         <system.serviceModel>  
          <services>  
          […]  
          </services>  
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="cbb24-223">Les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent aussi être configurées pour utiliser .asmx comme l'extension de leurs fichiers de service plutôt que .svc.</span><span class="sxs-lookup"><span data-stu-id="cbb24-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="cbb24-224">Cette option peut vous éviter d'avoir à modifier des clients configurés pour utiliser les URL de fichiers de service .asmx lors de la modification d'un service pour utiliser [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-224">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="cbb24-225">Développement client</span><span class="sxs-lookup"><span data-stu-id="cbb24-225">Client Development</span></span>  
 <span data-ttu-id="cbb24-226">Les clients pour les services Web ASP.NET sont générés à l'aide de l'outil de ligne de commande, WSDL.exe, qui fournit l'URL du fichier .asmx comme entrée.</span><span class="sxs-lookup"><span data-stu-id="cbb24-226">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="cbb24-227">L’outil correspondant fourni par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="cbb24-227">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="cbb24-228">Il génère un module de code avec la définition du contrat de service et la définition d'une classe de client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-228">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="cbb24-229">Il génère également un fichier de configuration avec l'adresse et la liaison du service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-229">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="cbb24-230">Pour programmer un client d'un service distant, il est généralement recommandé de programmer selon un modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="cbb24-230">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="cbb24-231">Le code généré par l’outil WSDL.exe fournit toujours un modèle synchrone et asynchrone par défaut.</span><span class="sxs-lookup"><span data-stu-id="cbb24-231">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="cbb24-232">Le code généré par le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut fournir un modèle.</span><span class="sxs-lookup"><span data-stu-id="cbb24-232">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="cbb24-233">Il fournit le modèle synchrone par défaut.</span><span class="sxs-lookup"><span data-stu-id="cbb24-233">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="cbb24-234">Si l'outil est exécuté avec le commutateur `/async`, le code généré fournit le modèle asynchrone.</span><span class="sxs-lookup"><span data-stu-id="cbb24-234">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="cbb24-235">Il n'y a aucune garantie que les noms dans les classes clientes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] générées par l'outil WSDL.exe d'ASP.NET, par défaut, correspondent aux noms dans les classes clientes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] générées par l'outil Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="cbb24-235">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="cbb24-236">En particulier, les noms des propriétés des classes qui doivent être sérialisées à l'aide du <xref:System.Xml.Serialization.XmlSerializer> reçoivent par défaut le suffixe Property dans le code généré par l'outil Svcutil.exe, ce qui n'est pas le cas avec l'outil WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="cbb24-236">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="cbb24-237">Représentation de message</span><span class="sxs-lookup"><span data-stu-id="cbb24-237">Message Representation</span></span>  
 <span data-ttu-id="cbb24-238">Les en-têtes des messages SOAP envoyés et reçus par les services Web ASP.NET peuvent être personnalisés.</span><span class="sxs-lookup"><span data-stu-id="cbb24-238">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="cbb24-239">Une classe est dérivée de <xref:System.Web.Services.Protocols.SoapHeader> pour définir la structure de l'en-tête, puis, le <xref:System.Web.Services.Protocols.SoapHeaderAttribute> est utilisé pour indiquer la présence de l'en-tête.</span><span class="sxs-lookup"><span data-stu-id="cbb24-239">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
public class SomeProtocol : SoapHeader  
{  
     public long CurrentValue;  
     public long Total;  
}  
  
[WebService]  
public interface IEcho  
{  
     SomeProtocol ProtocolHeader  
     {  
      get;  
     set;  
     }  
  
     [WebMethod]  
     [SoapHeader("ProtocolHeader")]  
     string PlaceOrders(PurchaseOrderType order);  
}  
  
public class Service: WebService, IEcho  
{  
     private SomeProtocol protocolHeader;  
  
     public SomeProtocol ProtocolHeader  
     {  
         get  
         {  
              return this.protocolHeader;  
         }  
  
         set  
         {  
              this.protocolHeader = value;  
         }  
     }  
  
     string PlaceOrders(PurchaseOrderType order)  
     {  
         long currentValue = this.protocolHeader.CurrentValue;  
     }  
}  
```  
  
 <span data-ttu-id="cbb24-240">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit les attributs, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>et <xref:System.ServiceModel.MessageBodyMemberAttribute> pour décrire la structure des messages SOAP envoyés et reçus par un service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-240">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
[DataContract]  
public class SomeProtocol  
{  
     [DataMember]  
     public long CurrentValue;  
     [DataMember]  
     public long Total;  
}  
  
[DataContract]  
public class Item  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
  
[MessageContract]  
public class ItemMesage  
{  
     [MessageHeader]  
     public SomeProtocol ProtocolHeader;  
     [MessageBody]  
     public Item Content;  
}  
  
[ServiceContract]  
public interface IItemService  
{  
     [OperationContract]  
     public void DeliverItem(ItemMessage itemMessage);  
}  
```  
  
 <span data-ttu-id="cbb24-241">Cette syntaxe génère une représentation explicite de la structure des messages, alors que la structure des messages est impliquée par le code d'un service Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-241">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="cbb24-242">De plus, dans la syntaxe ASP.NET, les en-têtes des messages sont représentés comme des propriétés du service, telles que la propriété `ProtocolHeader` dans l'exemple précédent, alors que dans la syntaxe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ils sont représentés plus correctement comme des propriétés de messages.</span><span class="sxs-lookup"><span data-stu-id="cbb24-242">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="cbb24-243">De plus, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autorise l'ajout d'en-têtes de message à la configuration de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cbb24-243">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
```xml  
<service name="Service ">  
     <endpoint   
      address="EchoService"  
      binding="basicHttpBinding"  
      contract="IEchoService ">  
      <headers>  
      <dsig:X509Certificate   
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">  
       ...  
      </dsig:X509Certificate>  
      </headers>  
     </endpoint>  
</service>  
```  
  
 <span data-ttu-id="cbb24-244">Cette option vous permet d'éviter toute référence aux en-têtes de protocole d'infrastructure dans le code pour un client ou un service : les en-têtes sont ajoutés aux messages selon le mode de configuration du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="cbb24-244">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="cbb24-245">Service Description</span><span class="sxs-lookup"><span data-stu-id="cbb24-245">Service Description</span></span>  
 <span data-ttu-id="cbb24-246">L'émission d'une demande HTTP GET pour le fichier .asmx d'un service Web ASP.NET avec la requête WSDL entraîne la génération de WSDL par ASP.NET pour décrire le service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-246">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="cbb24-247">Il retourne ce WSDL en réponse à la demande.</span><span class="sxs-lookup"><span data-stu-id="cbb24-247">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="cbb24-248">ASP.NET 2.0 permet de valider la conformité d'un service avec Basic Profile 1.1 de Web Services-Interoperability Organization (WS-I), et d'insérer une revendication que le service est conforme dans son WSDL.</span><span class="sxs-lookup"><span data-stu-id="cbb24-248">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="cbb24-249">Cette opération est effectuée à l'aide des paramètres `ConformsTo` et `EmitConformanceClaims` de l'attribut <xref:System.Web.Services.WebServiceBindingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-249">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="cbb24-250">Le WSDL généré par ASP.NET pour un service peut être personnalisé.</span><span class="sxs-lookup"><span data-stu-id="cbb24-250">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="cbb24-251">Les personnalisations s'effectuent en créant une classe dérivée de <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pour ajouter des éléments au WSDL.</span><span class="sxs-lookup"><span data-stu-id="cbb24-251">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="cbb24-252">L'émission d'une demande HTTP GET avec la requête WSDL pour le fichier .svc d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec un point de terminaison HTTP hébergé dans les services IIS 5.1, 6.0 ou WAS entraîne la réponse de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec du WSDL pour décrire le service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-252">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="cbb24-253">L'émission d'une demande HTTP GET avec la requête WSDL à l'adresse de base HTTP d'un service hébergé dans une application .NET a le même effet si httpGetEnabled a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="cbb24-253">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="cbb24-254">Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond également aux demandes WS-MetadataExchange avec du WSDL qu'il génère pour décrire un service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-254">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="cbb24-255">Les services Web ASP.NET n'offrent pas de prise en charge intégrée pour les demandes WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="cbb24-255">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="cbb24-256">Il est possible de personnaliser de manière extensive le WSDL généré par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cbb24-256">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="cbb24-257">La classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> fournit des fonctions pour personnaliser le WSDL.</span><span class="sxs-lookup"><span data-stu-id="cbb24-257">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="cbb24-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut aussi être configuré pour ne pas générer de WSDL, mais pour utiliser un fichier WSDL statique à une URL donnée.</span><span class="sxs-lookup"><span data-stu-id="cbb24-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DescriptionBehavior">  
     <metadataPublishing   
      enableMetadataExchange="true"   
      enableGetWsdl="true"   
      enableHelpPage="true"   
      metadataLocation=  
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>  
     </behavior>  
</behaviors>  
```  
  
## <a name="exception-handling"></a><span data-ttu-id="cbb24-259">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="cbb24-259">Exception Handling</span></span>  
 <span data-ttu-id="cbb24-260">Dans les services Web ASP.NET, les exceptions non prises en charge sont retournées aux clients comme des erreurs SOAP.</span><span class="sxs-lookup"><span data-stu-id="cbb24-260">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="cbb24-261">Vous pouvez aussi lever explicitement des instances de la classe <xref:System.Web.Services.Protocols.SoapException> et avoir plus de contrôle sur le contenu de l'erreur SOAP transmise au client.</span><span class="sxs-lookup"><span data-stu-id="cbb24-261">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="cbb24-262">Dans les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les exceptions non prises en charge ne sont pas retournées aux clients comme des erreurs SOAP afin d'empêcher d'exposer accidentellement des informations sensibles par l'intermédiaire des exceptions.</span><span class="sxs-lookup"><span data-stu-id="cbb24-262">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="cbb24-263">Un paramètre de configuration est fourni pour que les exceptions non prises en charge soient retournées aux clients à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="cbb24-263">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="cbb24-264">Pour retourner des erreurs SOAP aux clients, vous pouvez lever des instances du type générique, <xref:System.ServiceModel.FaultException%601>, à l'aide du type de contrat de données comme type générique.</span><span class="sxs-lookup"><span data-stu-id="cbb24-264">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="cbb24-265">Vous pouvez aussi ajouter des attributs <xref:System.ServiceModel.FaultContractAttribute> aux opérations pour spécifier les erreurs qu'une opération peut générer.</span><span class="sxs-lookup"><span data-stu-id="cbb24-265">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
[DataContract]  
public class MathFault  
{   
     [DataMember]  
     public string operation;  
     [DataMember]  
     public string problemType;  
}  
  
[ServiceContract]  
public interface ICalculator  
{  
     [OperationContract]  
     [FaultContract(typeof(MathFault))]  
     int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="cbb24-266">Cette opération entraîne la publication des erreurs possibles dans le WSDL pour le service, ce qui permet aux programmeurs du client d'anticiper sur les erreurs possibles à l'issue d'une opération, et d'écrire les instructions catch appropriées.</span><span class="sxs-lookup"><span data-stu-id="cbb24-266">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
try  
{  
     result = client.Divide(value1, value2);  
}  
catch (FaultException<MathFault> e)  
{  
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "  
  + e.Detail.operation   
  + ". Problem: "   
  + e.Detail.problemType);  
}  
```  
  
## <a name="state-management"></a><span data-ttu-id="cbb24-267">Gestion des états</span><span class="sxs-lookup"><span data-stu-id="cbb24-267">State Management</span></span>  
 <span data-ttu-id="cbb24-268">La classe utilisée pour implémenter un service Web ASP.NET peut être dérivée de <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-268">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="cbb24-269">Dans ce cas, la classe peut être programmée pour utiliser la propriété Context de la classe de base <xref:System.Web.Services.WebService> pour accéder à un objet <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-269">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="cbb24-270">L'objet <xref:System.Web.HttpContext> peut être utilisé pour mettre à jour et récupérer des informations d'état d'application en utilisant sa propriété Application, et pour mettre à jour et récupérer des informations d'état de session en utilisant sa propriété Session.</span><span class="sxs-lookup"><span data-stu-id="cbb24-270">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="cbb24-271">ASP.NET permet un contrôle important sur l'emplacement de stockage réel des informations d'état de session accessibles à l'aide de la propriété Session du <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-271">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="cbb24-272">Elles peuvent être stockées dans des cookies, une base de données, la mémoire du serveur actuel ou la mémoire d'un serveur désigné.</span><span class="sxs-lookup"><span data-stu-id="cbb24-272">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="cbb24-273">Le choix s'opère dans le fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-273">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="cbb24-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des objets extensibles pour la gestion d'état.</span><span class="sxs-lookup"><span data-stu-id="cbb24-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="cbb24-275">Les objets extensibles sont des objets qui implémentent <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-275">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="cbb24-276">Les objets extensibles les plus importants sont <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-276">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="cbb24-277">`ServiceHostBase` vous permet de maintenir l'état accessible par toutes les instances de tous les types de services sur le même hôte, alors que `InstanceContext` vous permet de maintenir l'état accessible par tout code s'exécutant dans la même instance d'un type de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-277">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="cbb24-278">Dans ce contexte, le type de service, `TradingSystem`, possède un <xref:System.ServiceModel.ServiceBehaviorAttribute> qui spécifie que les appels généraux de la même instance cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont acheminés vers la même instance du type de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-278">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="cbb24-279">La classe, `DealData`, définit l'état accessible par tout code qui s'exécute dans la même instance d'un type de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-279">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="cbb24-280">Dans le code du type de service qui implémente l'une des opérations du contrat de service, un objet d'état `DealData` est ajouté à l'état de l'instance actuelle du type de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-280">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="cbb24-281">Cet objet d'état peut être ensuite récupéré et modifié par le code qui implémente une autre opération des opérations du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="cbb24-281">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="cbb24-282">Si ASP.NET fournit le contrôle sur l'emplacement réel de stockage des informations d'état dans la classe <xref:System.Web.HttpContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], du moins dans sa version initiale, ne fournit aucun contrôle sur l'emplacement de stockage des objets extensibles.</span><span class="sxs-lookup"><span data-stu-id="cbb24-282">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="cbb24-283">Il n'en faut pas plus pour sélectionner le mode de compatibilité ASP.NET pour un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-283">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="cbb24-284">Si la gestion d'état configurable est impérative, choisir ensuite le mode de compatibilité ASP.NET vous permet d'utiliser les fonctions de la classe <xref:System.Web.HttpContext> exactement telles qu'elles sont utilisées dans ASP.NET, et de configurer aussi l'emplacement de stockage des informations d'état gérées à l'aide de la classe <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-284">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="cbb24-285">Sécurité</span><span class="sxs-lookup"><span data-stu-id="cbb24-285">Security</span></span>  
 <span data-ttu-id="cbb24-286">Les options permettant de sécuriser les services Web ASP.NET sont celles qui permettent de sécuriser toute application IIS.</span><span class="sxs-lookup"><span data-stu-id="cbb24-286">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="cbb24-287">Comme les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être hébergées non seulement dans les services IIS mais aussi dans un fichier exécutable .NET, les options permettant de sécuriser des applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doivent être indépendantes des fonctions des services IIS.</span><span class="sxs-lookup"><span data-stu-id="cbb24-287">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="cbb24-288">Toutefois, les fonctions fournies pour les services Web ASP.NET sont aussi disponibles pour les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-288">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="cbb24-289">Sécurité : authentification</span><span class="sxs-lookup"><span data-stu-id="cbb24-289">Security: Authentication</span></span>  
 <span data-ttu-id="cbb24-290">Les services IIS fournissent des fonctions de contrôle de l'accès aux applications qui permettent de sélectionner un accès anonyme ou un ensemble de modes d'authentification : l'authentification Windows, l'authentification Digest, l'authentification de base et l'authentification .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="cbb24-290">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="cbb24-291">L'option d'authentification Windows peut être utilisée pour contrôler l'accès aux services Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-291">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="cbb24-292">Toutefois, lorsque les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont hébergées dans les services IIS, ces services doivent être configurés pour autoriser l'accès anonyme à l'application, afin que l'authentification puisse être gérée par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], qui prend en charge l'authentification Windows entre autres options.</span><span class="sxs-lookup"><span data-stu-id="cbb24-292">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="cbb24-293">Les autres options intégrées incluent les jetons de nom d'utilisateur, les certificats X.509, les jetons SAML et la carte CardSpace, mais il est possible de définir aussi des mécanismes d'authentification personnalisés.</span><span class="sxs-lookup"><span data-stu-id="cbb24-293">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="cbb24-294">Sécurité : emprunt d'identité</span><span class="sxs-lookup"><span data-stu-id="cbb24-294">Security: Impersonation</span></span>  
 <span data-ttu-id="cbb24-295">ASP.NET fournit un élément d'identité qui permet à un service Web ASP.NET d'emprunter à un utilisateur particulier son identité ou les informations d'identification de l'utilisateur fournies dans la demande actuelle.</span><span class="sxs-lookup"><span data-stu-id="cbb24-295">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="cbb24-296">Cet élément peut être utilisé pour configurer l'emprunt d'identité dans les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui s'exécutent en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-296">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="cbb24-297">Le système de configuration [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit son propre élément d'identité pour désigner un utilisateur particulier dont l'identité est empruntée.</span><span class="sxs-lookup"><span data-stu-id="cbb24-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="cbb24-298">De plus, les clients et les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent être configurés indépendamment pour l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="cbb24-298">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="cbb24-299">Les clients peuvent être configurés pour emprunter l'identité de l'utilisateur actuel lorsqu'ils transmettent des demandes.</span><span class="sxs-lookup"><span data-stu-id="cbb24-299">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="cbb24-300">Les opérations de service peuvent être configurées pour emprunter les informations d'identification de l'utilisateur qui fourni la demande actuelle.</span><span class="sxs-lookup"><span data-stu-id="cbb24-300">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="cbb24-301">Sécurité : autorisation à l'aide des listes de contrôle d'accès</span><span class="sxs-lookup"><span data-stu-id="cbb24-301">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="cbb24-302">Les listes de contrôle d'accès (ACL) peuvent être utilisées pour restreindre l'accès aux fichiers .asmx.</span><span class="sxs-lookup"><span data-stu-id="cbb24-302">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="cbb24-303">Toutefois, les listes de contrôle d'accès sur les fichiers .svc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont ignorées sauf en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-303">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="cbb24-304">Sécurité : autorisation basée sur les rôles</span><span class="sxs-lookup"><span data-stu-id="cbb24-304">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="cbb24-305">L'option d'authentification IIS Windows peut être utilisée conjointement avec l'élément d'autorisation fourni par le langage de configuration ASP.NET pour faciliter l'autorisation basée sur les rôles pour les services Web ASP.NET selon les groupes Windows auxquels les utilisateurs sont assignés.</span><span class="sxs-lookup"><span data-stu-id="cbb24-305">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="cbb24-306">ASP.NET 2.0 introduit un mécanisme plus général d'autorisation basée sur les rôles : les fournisseurs de rôles.</span><span class="sxs-lookup"><span data-stu-id="cbb24-306">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="cbb24-307">Les fournisseurs de rôles sont des classes qui implémentent toutes une interface de base pour s'informer des rôles auxquels un utilisateur est assigné, mais chaque fournisseur de rôle sait comment récupérer ces information issues d'une source différente.</span><span class="sxs-lookup"><span data-stu-id="cbb24-307">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="cbb24-308">ASP.NET 2.0 fournit un fournisseur de rôles qui peut récupérer des affectations de rôle d'une base de données Microsoft SQL Server, ainsi qu'un autre fournisseur qui peut récupérer des affectations de rôles issues du Gestionnaire d'autorisations Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="cbb24-308">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="cbb24-309">En fait, le mécanisme du fournisseur de rôle peut être utilisé indépendamment d'ASP.NET dans une application .NET, ainsi que dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbb24-309">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="cbb24-310">L'exemple de configuration suivant pour une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] montre comment l'utilisation d'un fournisseur de rôles ASP.NET est une option sélectionnée au moyen de l'objet <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-310">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
     <services>  
         <service name="Service.ResourceAccessServiceType"   
             behaviorConfiguration="ServiceBehavior">  
             <endpoint   
              address="ResourceAccessService"   
              binding="wsHttpBinding"   
              contract="Service.IResourceAccessContract"/>  
         </service>  
     </services>  
     <behaviors>  
       <behavior name="ServiceBehavior">  
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>  
      </behavior>  
     </behaviors>  
</system.serviceModel>  
```  
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="cbb24-311">Sécurité : autorisation basée sur les revendications</span><span class="sxs-lookup"><span data-stu-id="cbb24-311">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="cbb24-312">L'une des innovations les plus importantes de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est la prise en charge complète permettant d'autoriser l'accès aux ressources protégées basées sur des revendications.</span><span class="sxs-lookup"><span data-stu-id="cbb24-312">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="cbb24-313">Les revendications se composent d'un type, d'un droit et d'une valeur, un permis de conduire, par exemple.</span><span class="sxs-lookup"><span data-stu-id="cbb24-313">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="cbb24-314">Elle produit un jeu de revendications relatives au porteur, dont l'une d'entre elles est la date de naissance du porteur.</span><span class="sxs-lookup"><span data-stu-id="cbb24-314">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="cbb24-315">Le type de cette revendication est la date de naissance, la valeur de la revendication est la date de naissance du conducteur.</span><span class="sxs-lookup"><span data-stu-id="cbb24-315">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="cbb24-316">Le droit que confère une revendication au porteur spécifie ce que le porteur peut faire avec la valeur de la revendication.</span><span class="sxs-lookup"><span data-stu-id="cbb24-316">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="cbb24-317">Dans le cas de la revendication de la date de naissance du conducteur, ce droit est la propriété : le conducteur possède cette date de naissance mais il ne peut pas, par exemple, la modifier.</span><span class="sxs-lookup"><span data-stu-id="cbb24-317">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="cbb24-318">L'autorisation basée sur les revendications intègre l'autorisation basée sur les rôles, parce que les rôles sont un type de revendication.</span><span class="sxs-lookup"><span data-stu-id="cbb24-318">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="cbb24-319">L'autorisation basée sur les revendications s'accomplit en comparant un jeu de revendications aux spécifications d'accès de l'opération et, selon le résultat de cette comparaison, l'accès à l'opération est accordé ou refusé.</span><span class="sxs-lookup"><span data-stu-id="cbb24-319">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="cbb24-320">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous pouvez spécifier une classe pour exécuter l'autorisation basée sur des revendications, là encore en assignant une valeur à la propriété `ServiceAuthorizationManager` de <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cbb24-320">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="cbb24-321">Les classes utilisées pour exécuter l'autorisation basée sur les revendications doivent dériver de <xref:System.ServiceModel.ServiceAuthorizationManager>, qui contient une méthode à substituer, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="cbb24-321">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="cbb24-322"> appelle cette méthode chaque fois qu'une opération du service est invoquée et fournit un objet <xref:System.ServiceModel.OperationContext>, qui contient les revendications de l'utilisateur dans sa propriété `ServiceSecurityContext.AuthorizationContext`.</span><span class="sxs-lookup"><span data-stu-id="cbb24-322"> calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="cbb24-323"> est chargé d'assembler les revendications sur l'utilisateur à partir du jeton de sécurité fourni par celui-ci pour l'authentification. Il reste ensuite à évaluer la validité de ces revendications pour effectuer l'opération en question.</span><span class="sxs-lookup"><span data-stu-id="cbb24-323"> does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="cbb24-324">Le fait que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assemble automatiquement des revendications de tout type de jeton de sécurité est une innovation très significative, parce qu'elle permet au code pour l'autorisation basée sur les revendications d'être entièrement indépendant du mécanisme d'authentification.</span><span class="sxs-lookup"><span data-stu-id="cbb24-324">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="cbb24-325">Par contraste, l'autorisation à l'aide des listes de contrôle d'accès ou des rôles dans ASP.NET est étroitement liée à l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="cbb24-325">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="cbb24-326">Sécurité : confidentialité</span><span class="sxs-lookup"><span data-stu-id="cbb24-326">Security: Confidentiality</span></span>  
 <span data-ttu-id="cbb24-327">La confidentialité des messages échangés avec les services Web ASP.NET peut être garantie au niveau du transport en configurant l'application dans les services IIS pour qu'elle utilise le protocole HTTPS (Secure Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="cbb24-327">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="cbb24-328">Il en va de même pour les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergées dans les services IIS.</span><span class="sxs-lookup"><span data-stu-id="cbb24-328">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="cbb24-329">Cependant, les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergées en dehors des services IIS peuvent également être configurées pour utiliser un protocole de transport sécurisé.</span><span class="sxs-lookup"><span data-stu-id="cbb24-329">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="cbb24-330">Plus important, les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent aussi être configurées pour sécuriser les messages avant qu'ils soient transportés, à l'aide du protocole WS-Security.</span><span class="sxs-lookup"><span data-stu-id="cbb24-330">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="cbb24-331">La sécurisation uniquement du corps d'un message à l'aide de WS-Security lui permet d'être transmis confidentiellement par des intermédiaires avant d'atteindre sa destination finale.</span><span class="sxs-lookup"><span data-stu-id="cbb24-331">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="cbb24-332">Globalisation</span><span class="sxs-lookup"><span data-stu-id="cbb24-332">Globalization</span></span>  
 <span data-ttu-id="cbb24-333">Le langage de configuration ASP.NET vous permet de spécifier la culture pour les services individuels.</span><span class="sxs-lookup"><span data-stu-id="cbb24-333">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="cbb24-334">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge ce paramètre de configuration sauf en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cbb24-334">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="cbb24-335">Pour localiser un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui n'utilise pas le mode de compatibilité ASP.NET, compilez le type de service dans des assemblys spécifiques à la culture et utilisez des points de terminaison séparés spécifiques à la culture pour chaque assembly spécifique à la culture.</span><span class="sxs-lookup"><span data-stu-id="cbb24-335">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb24-336">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbb24-336">See Also</span></span>  
 [<span data-ttu-id="cbb24-337">Comparaison des services web ASP.NET et de WCF en fonction de l’objectif et des normes utilisées</span><span class="sxs-lookup"><span data-stu-id="cbb24-337">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
