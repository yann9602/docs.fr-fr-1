---
title: "Comment&#160;: s&#233;rialiser et d&#233;s&#233;rialiser des donn&#233;es JSON | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Comment&#160;: s&#233;rialiser et d&#233;s&#233;rialiser des donn&#233;es JSON
JSON (JavaScript Object Notation) est un format d'encodage de données efficace qui permet l'échange rapide de petites quantités de données entre les navigateurs clients et les services Web compatibles AJAX.  
  
 Cette rubrique montre comment sérialiser des objets de type .NET dans des données encodées JSON et ensuite désérialiser les données au format JSON en instances de types .NET à l’aide de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Cet exemple utilise un contrat de données pour montrer la sérialisation et la désérialisation d'un type `Person` défini par l'utilisateur.  
  
 Normalement, la sérialisation et la désérialisation JSON sont contrôlées automatiquement par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] lorsque vous utilisez les types de contrats de données dans les opérations de service exposées sur des points de terminaison compatibles AJAX. Toutefois, dans certains cas, vous devez travailler directement avec les données JSON ; c'est le scénario abordé dans cette rubrique.  
  
> [!NOTE]
>  Si une erreur se produit pendant la sérialisation d'une réponse sortante sur le serveur ou si l'opération de réponse lève une quelconque exception, il se peut qu'elle ne soit pas retournée au client sous forme d'erreur.  
  
 Cette rubrique est basée sur le [sérialisation JSON](../../../../docs/framework/wcf/samples/json-serialization.md) exemple.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Pour définir le contrat de données pour une personne  
  
1.  Définissez le contrat de données pour `Person` en attachant le <xref:System.Runtime.Serialization.DataContractAttribute> à la classe et <xref:System.Runtime.Serialization.DataMemberAttribute> attribut aux membres que vous souhaitez sérialiser. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]contrats de données, consultez [concevoir des contrats de Service](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
    ```  
    [DataContract]  
        internal class Person  
        {  
            [DataMember]  
            internal string name;  
  
            [DataMember]  
            internal int age;  
        }  
    ```  
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>Pour sérialiser une instance de type Person à JSON  
  
1.  Créez une instance du type `Person`.  
  
    ```  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Sérialiser les `Person` objet pour un flux de mémoire à l’aide de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Utilisez le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> méthode pour écrire des données JSON dans le flux.  
  
    ```  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  Affichez la sortie JSON.  
  
    ```  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Pour désérialiser une instance de type Person depuis JSON  
  
1.  Désérialisez les données codées avec JSON dans une nouvelle instance de `Person` à l’aide de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> procédé de la <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Affichez les résultats.  
  
    ```  
    Console.Write("Deserialized back, got name=");  
    Console.Write(p2.name);  
    Console.Write(", age=");  
    Console.WriteLine(p2.age);  
    ```  
  
## <a name="example"></a>Exemple  
  
```  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
  
```  
  
> [!NOTE]
>  Le sérialiseur JSON lève une exception de sérialisation pour les contrats de données dont plusieurs membres portent le même nom, comme illustré dans l'exemple de code suivant.  
  
```  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}  
[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)   
 [Prise en charge de JSON et autres données de Formats de transfert](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)