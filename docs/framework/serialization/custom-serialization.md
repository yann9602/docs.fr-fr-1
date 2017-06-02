---
title: "S&#233;rialisation personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation binaire, contrôler"
  - "sérialisation binaire, sérialisation personnalisée"
  - "sérialisation personnalisée"
  - "ISerializable (interface), sérialisation personnalisée"
  - "OnDeserializedAttribute (classe), sérialisation personnalisée"
  - "OnDeserializingAttribute (classe), sérialisation personnalisée"
  - "OnSerializedAttribute (classe), sérialisation personnalisée"
  - "OnSerializingAttribute (classe), sérialisation personnalisée"
  - "OptionalFieldAttribute (classe), sérialisation personnalisée"
  - "sérialisation, contrôler"
  - "sérialisation, sérialisation personnalisée"
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# S&#233;rialisation personnalis&#233;e
La sérialisation personnalisée est le processus de contrôle de la sérialisation et désérialisation d'un type.En contrôlant la sérialisation, il est possible de garantir la compatibilité de sérialisation \(capacité de sérialisation et désérialisation entre des versions d'un type\) sans interrompre la fonctionnalité principale du type.Par exemple, il peut y avoir uniquement deux champs dans la première version d'un type.Dans la version suivante d'un type, plusieurs champs supplémentaires sont ajoutés.La deuxième version d'une application doit néanmoins être en mesure de sérialiser et désérialiser les deux types.Les sections suivantes décrivent comment contrôler la sérialisation.  
  
> [!IMPORTANT]
>  Dans les versions antérieures à .NET Framework 4.0, la sérialisation de données utilisateur personnalisées dans un assembly  d'un niveau de confiance partiel était obtenue à l'aide de la <xref:System.Exception.GetObjectData%2A> method?qualifyHint=False&autoUpgrade=True.Depuis la version 4.0, cette méthode est marquée avec l'attribut <xref:System.Security.SecurityCriticalAttribute>, ce qui empêche l'exécution dans les assemblys d'un niveau de confiance partiel.Pour contourner cette condition, implémentez l'interface <xref:System.Runtime.Serialization.ISafeSerializationData>.  
  
## Exécution de méthodes personnalisées pendant et après la sérialisation  
 La méthode conseillée la plus simple \(présentée dans la version 2.0 du .NET Framework\) consiste à appliquer les attributs suivants aux méthodes utilisées pour corriger des données pendant et après la sérialisation :  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Ces attributs permettent au type de participer à l'une ou à l'ensemble des quatre phases des processus de sérialisation et de désérialisation.Les attributs spécifient les méthodes du type qui doivent être invoquées pendant chaque phase.Les méthodes n'accèdent pas au flux de données de sérialisation mais vous permettent en revanche de modifier l'objet avant et après la sérialisation, ou avant et après la désérialisation.Les attributs peuvent être appliqués à tous les niveaux de la hiérarchie d'héritage de type, et chaque méthode est appelée dans la hiérarchie de la base au plus dérivé.Ce mécanisme évite la complexité et tous les problèmes résultant de l'implémentation de l'interface <xref:System.Runtime.Serialization.ISerializable> en rendant l'implémentation la plus dérivée responsable de la sérialisation et de la désérialisation.En outre, ce mécanisme permet aux formateurs d'ignorer le remplissage de champs et la récupération du flux de données de sérialisation.Pour obtenir des informations et des exemples concernant le contrôle de la sérialisation et de la désérialisation, cliquez sur l'un des liens précédents.  
  
 De plus, lorsque vous ajoutez un nouveau champ à un type sérialisable existant, appliquez l'attribut <xref:System.Runtime.Serialization.OptionalFieldAttribute> au champ.<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignorent l'absence du champ lorsqu'un flux de données dont le nouveau champ est manquant est traité.  
  
## Implémentation de l'interface ISerializable  
 L'autre méthode permettant de contrôler la sérialisation s'effectue en implémentant l'interface [ISerializable](frlrfSystemRuntimeSerializationISerializableClassTopic) sur un objet.Toutefois, notez que la méthode de la section précédente remplace cette méthode pour contrôler la sérialisation.  
  
 De plus, vous ne devez pas utiliser la sérialisation par défaut sur une classe marquée avec l'attribut [Serializable](frlrfSystemSerializableAttributeClassTopic) et présentant une sécurité déclarative ou impérative au niveau de la classe ou sur ses constructeurs.En revanche, ces classes doivent toujours implémenter l'interface **ISerializable**.  
  
 L'implémentation d'**ISerializable** implique l'implémentation de la méthode [GetObjectData](frlrfSystemRuntimeSerializationISerializableClassGetObjectDataTopic) et l'utilisation d'un constructeur spécial lorsque l'objet est désérialisé.L'exemple de code suivant indique comment implémenter **ISerializable** sur la classe `MyObject` d'une section précédente.  
  
```csharp  
[Serializable]  
public class MyObject : ISerializable   
{  
  public int n1;  
  public int n2;  
  public String str;  
  
  public MyObject()  
  {  
  }  
  
  protected MyObject(SerializationInfo info, StreamingContext context)  
  {  
    n1 = info.GetInt32("i");  
    n2 = info.GetInt32("j");  
    str = info.GetString("k");  
  }  
[SecurityPermissionAttribute(SecurityAction.Demand,   
SerializationFormatter =true)]  
  
public virtual void GetObjectData(SerializationInfo info, StreamingContext context)  
  {  
    info.AddValue("i", n1);  
    info.AddValue("j", n2);  
    info.AddValue("k", str);  
  }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class MyObject  
    Implements ISerializable  
    Public n1 As Integer  
    Public n2 As Integer  
    Public str As String  
  
    Public Sub New()   
    End Sub   
  
    Protected Sub New(ByVal info As SerializationInfo, _  
    ByVal context As StreamingContext)   
        n1 = info.GetInt32("i")  
        n2 = info.GetInt32("j")  
        str = info.GetString("k")  
    End Sub 'New  
  
    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Public Overridable Sub GetObjectData(ByVal info As _  
    SerializationInfo, ByVal context As StreamingContext)   
        info.AddValue("i", n1)  
        info.AddValue("j", n2)  
        info.AddValue("k", str)  
    End Sub   
End Class  
```  
  
 Lorsque **GetObjectData** est appelée pendant la sérialisation, vous êtes chargé de remplir le [SerializationInfo](frlrfSystemRuntimeSerializationSerializationInfoClassTopic) fourni avec l'appel à méthode.Ajoutez les variables à sérialiser sous forme de paires de noms et de valeurs.Tout texte peut être utilisé comme nom.Vous pouvez décider quelles variables membres sont ajoutées au **SerializationInfo**, à condition qu'il y ait suffisamment de données sérialisées pour restaurer l'objet pendant la désérialisation.Les classes dérivées doivent appeler la méthode **GetObjectData** sur l'objet de base si ce dernier implémente **ISerializable.**  
  
 Notez que la sérialisation peut permettre à un autre code d'afficher ou de modifier des données d'instance d'objet qui seraient autrement inaccessibles.Par conséquent, le code qui exécute la sérialisation requiert que [SecurityPermission](frlrfSystemSecurityPermissionsSecurityPermissionClassTopic) soit définie sur l'indicateur [SerializationFormatter](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic).Dans le cadre de la stratégie par défaut, cette autorisation n'est pas accordée à du code téléchargé depuis Internet ou un intranet ; seul le code sur l'ordinateur local reçoit cette autorisation.La méthode **GetObjectData** doit être protégée explicitement en demandant que **SecurityPermission** soit définie sur l'indicateur **SerializationFormatter** ou en demandant d'autres autorisations qui permettent de protéger spécifiquement des données privées.  
  
 Si un champ privé stocke des informations sensibles, vous devez demander les autorisations appropriées sur **GetObjectData** pour protéger les données.Rappelez\-vous que le code auquel a été attribuée l'autorisation **SecurityPermission** définie sur l'indicateur **SerializationFormatter** peut afficher et modifier les données stockées dans les champs privés.Un appelant malveillant qui a obtenu l'autorisation **SecurityPermission** peut consulter des données telles que les emplacements de répertoire cachés ou les autorisations accordées et utiliser ces données pour exploiter une faille de sécurité sur l'ordinateur.Pour obtenir une liste complète des indicateurs d'autorisation de sécurité que vous pouvez spécifier, consultez l'[énumération SecurityPermissionFlag](frlrfSystemSecurityPermissionsSecurityPermissionFlagClassTopic).  
  
 Il convient de souligner que lorsque **ISerializable** est ajoutée à une classe, vous devez implémenter **GetObjectData** et le constructeur spécial.Le compilateur vous prévient si **GetObjectData** est manquante.Toutefois, parce qu'il est impossible de mettre en œuvre l'implémentation d'un constructeur, aucun avertissement n'est fourni si le constructeur est absent, et une exception est levée lorsqu'une tentative est faite pour désérialiser une classe sans le constructeur.  
  
 La conception actuelle a priorité sur une méthode <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> pour contourner les problèmes potentiels de sécurité et de versioning.Par exemple, une méthode [SetObjectData](frlrfSystemRuntimeSerializationISerializationSurrogateClassSetObjectDataTopic) doit être publique si elle est définie dans le cadre d'une interface. Ainsi, les utilisateurs doivent écrire du code pour éviter que la méthode **SetObjectData** soit appelée plusieurs fois.Sinon, une application malveillante qui appelle la méthode **SetObjectData** sur un objet du processus d'exécution d'une opération peut provoquer des problèmes potentiels.  
  
 Pendant la désérialisation, **SerializationInfo** est transmis à la classe à l'aide du constructeur prévu à cette fin.Toutes les contraintes de visibilité imposées au constructeur sont ignorées lorsque l'objet est désérialisé. Vous pouvez donc marquer la classe comme publique, protégée, interne ou privée.Toutefois, la méthode conseillée consiste à protéger le constructeur tant que la classe n'est pas scellée. Le cas échéant, le constructeur doit être marqué comme privé.Le constructeur doit également exécuter une validation de saisie complète.Pour éviter une utilisation incorrecte par un code malveillant, le constructeur doit appliquer les mêmes vérifications de sécurité et autorisations nécessaires pour obtenir une instance de la classe utilisant tout autre constructeur.Si vous ne suivez pas cette recommandation, le code malveillant peut présérialiser un objet, obtenir le contrôle avec **SecurityPermission** définie sur l'indicateur **SerializationFormatter** et désérialiser l'objet sur un ordinateur client en contournant toute sécurité qui aurait été appliquée pendant la construction d'instance standard à l'aide d'un constructeur public.  
  
 Pour restaurer l'état de l'objet, récupérez simplement les valeurs des variables de **SerializationInfo** à l'aide des noms utilisés pendant la sérialisation.Si la classe de base implémente **ISerializable**, le constructeur de base doit être appelé pour permettre à l'objet de base de restaurer ses variables.  
  
 Lorsque vous dérivez une nouvelle classe d'une classe qui implémente **ISerializable,** la classe dérivée doit implémenter aussi bien le constructeur que la méthode **GetObjectData** si elle possède des variables qui doivent être sérialisées.L'exemple de code suivant illustre la procédure à l'aide de la classe `MyObject` montrée précédemment.  
  
```csharp  
[Serializable]  
public class ObjectTwo : MyObject  
{  
    public int num;  
  
    public ObjectTwo() : base()  
    {  
    }  
  
    protected ObjectTwo(SerializationInfo si,   
    StreamingContext context) : base(si,context)  
    {  
        num = si.GetInt32("num");  
    }  
[SecurityPermissionAttribute(SecurityAction.Demand,  
SerializationFormatter = true)]  
    public override void GetObjectData(SerializationInfo si,   
    StreamingContext context)  
    {  
        base.GetObjectData(si,context);  
        si.AddValue("num", num);  
    }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class ObjectTwo  
    Inherits MyObject  
    Public num As Integer  
  
    Public Sub New()   
  
    End Sub       
  
    Protected Sub New(ByVal si As SerializationInfo, _  
    ByVal context As StreamingContext)   
        MyBase.New(si, context)  
        num = si.GetInt32("num")      
    End Sub   
  
    <SecurityPermissionAttribute(SecurityAction.Demand, _  
    SerializationFormatter := True)>  _  
    Public Overrides Sub GetObjectData(ByVal si As _  
    SerializationInfo, ByVal context As StreamingContext)   
        MyBase.GetObjectData(si, context)  
        si.AddValue("num", num)      
    End Sub   
End Class  
```  
  
 N'oubliez pas d'appeler la classe de base dans le constructeur de désérialisation.Sinon, le constructeur de la classe de base n'est jamais appelé et l'objet n'est pas entièrement construit après la désérialisation.  
  
 Les objets sont reconstruits à l'envers et les méthodes d'appel au cours de la désérialisation peuvent avoir des effets secondaires indésirables, car les méthodes appelées peuvent se rapporter aux références d'objet qui n'ont pas été désérialisées au moment de l'appel.Si la classe qui est désérialisée implémente [IDeserializationCallback](frlrfsystemruntimeserializationideserializationcallbackclasstopic), la méthode [OnDeserialization](frlrfSystemRuntimeSerializationIDeserializationCallbackClassOnDeserializationTopic) est appelée automatiquement une fois le graphique d'objets entier désérialisé.À ce stade, tous les objets enfants référencés ont été restaurés complètement.Une table de hachage est un exemple typique d'une classe difficile à désérialiser sans utiliser l'écouteur d'événements.Il est facile de récupérer les clés et valeurs paires pendant la désérialisation, mais l'ajout de ces objets à la table de hachage peut provoquer des problèmes. En effet, il n'y a aucune garantie que les classes dérivées de la table de hachage sont désérialisées.Par conséquent, les méthodes d'appel sur une table de hachage ne sont pas recommandées à ce stade.  
  
## Voir aussi  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)   
 [Code Access Security](http://msdn.microsoft.com/fr-fr/23a20143-241d-4fe5-9d9f-3933fd594c03)