---
title: "S&#233;rialisation de base, exemple de technologie | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# S&#233;rialisation de base, exemple de technologie
[Télécharger l'exemple](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 Cet exemple montre la capacité du Common Language Runtime à sérialiser un graphique d'objets en mémoire dans un flux.Cet exemple peut utiliser <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour la sérialisation.Une liste liée, remplie de données, est sérialisée ou désérialisée dans un flux de fichiers ou à partir de celui\-ci.Dans les deux cas, la liste est affichée afin que vous puissiez consulter les résultats.Il s'agit d'une liste liée de type `LinkedList`, un type défini par cet exemple.  
  
 Pour plus d'informations sur la sérialisation, consultez les commentaires inclus dans les fichiers de code source et dans les fichiers build\-proj.  
  
### Pour générer l'exemple à partir de l'invite de commandes  
  
1.  Accédez à l'un des sous\-répertoires spécifiques aux différents langages dans le répertoire Technologies\\Serialization\\Runtime Serialization\\Basic, à l'aide de l'invite de commandes.  
  
2.  Tapez **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** ou **msbuild SerializationVB.sln** à la ligne de commande, selon votre choix de langage de programmation.  
  
### Pour générer l'exemple à l'aide de Visual Studio  
  
1.  Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez à l'un des sous\-répertoires spécifiques aux différents langages de l'exemple.  
  
2.  Double\-cliquez sur l'icône du fichier SerializationCS.sln, SerializationJSL.sln ou SerializationVB.sln, selon votre choix de langage de programmation, pour ouvrir le fichier dans Visual Studio.  
  
3.  Dans le menu **Générer**, sélectionnez **Générer la solution**.  
  
 L'exemple d'application est généré dans le sous\-répertoire \\bin ou \\bin\\Debug par défaut.  
  
### Pour exécuter l'exemple  
  
1.  Accédez au répertoire qui contient le fichier exécutable créé.  
  
2.  Tapez **Serialization.exe** ainsi que les valeurs de paramètre requis, dans la ligne de commande.  
  
    > [!NOTE]
    >  Cet exemple génère une application console.Vous devez la lancer à l'aide de l'invite de commandes pour pouvoir afficher sa sortie.  
  
## Notes  
 L'exemple d'application accepte des paramètres de ligne de commande indiquant le test à exécuter.Pour sérialiser une liste de 10 nœuds dans un fichier nommé **Test.xml** à l'aide du formateur SOAP, utilisez les paramètres **sx Test.xml 10**.  
  
 Par exemple :  
  
 **Serialize.exe \- sx Test.xml 10**  
  
 Pour désérialiser le fichier **Test.xml** de l'exemple précédent, utilisez les paramètres **dx Test.xml**.  
  
 Par exemple :  
  
 **Serialize.exe \- dx Test.xml**  
  
 Dans les deux exemples précités, la lettre "x" dans le commutateur de ligne de commande indique que vous souhaitez effectuer une sérialisation SOAP XML.Vous pouvez utiliser à la place la lettre "b" pour effectuer une sérialisation binaire.Si vous souhaitez effectuer une sérialisation avec un très grand nombre de nœuds, il peut être intéressant de rediriger la sortie de console vers un fichier.  
  
 Par exemple :  
  
 **Serialize.exe \-sb Test.bin 10000 \>fichierquelconque.txt**  
  
 Les éléments de la liste suivante décrivent brièvement les classes et les technologies utilisées par cet exemple.  
  
-   Sérialisation du runtime  
  
    -   <xref:System.Runtime.Serialization.IFormatter> Utilisé pour référencer un objet <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Utilisé pour sérialiser une liste liée dans un flux au format binaire.Le formateur binaire utilise un format reconnu uniquement par le type <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.Toutefois, les données sont concises.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Utilisé pour sérialiser une liste liée dans un flux au format SOAP.SOAP est un format standard.  
  
-   E\/S de flux  
  
    -   <xref:System.IO.Stream> Utilisé pour effectuer la sérialisation et la désérialisation.Le flux spécifique utilisé dans cet exemple est de type <xref:System.IO.FileStream>.Toutefois, la sérialisation peut être utilisée avec n'importe quel type dérivé de <xref:System.IO.Stream>.  
  
    -   <xref:System.IO.File> Utilisé pour créer des objets <xref:System.IO.FileStream> afin de lire et de créer des fichiers sur le disque.  
  
    -   <xref:System.IO.FileStream> Utilisé pour sérialiser et désérialiser des listes liées.  
  
## Voir aussi  
 [Classe BinaryFormatter](frlrfSystemRuntimeSerializationFormattersBinaryBinaryFormatterClassTopic)   
 [Classe de fichier](frlrfSystemIOFileClassTopic)   
 [Classe FileStream](frlrfSystemIOFileStreamClassTopic)   
 [Interface IFormatter](frlrfSystemRuntimeSerializationIFormatterClassTopic)   
 [Classe aléatoire](https://msdn.microsoft.com/en-us/library/system.random.aspx)   
 [Attribut SerializableAttribute](frlrfSystemSerializableAttributeClassTopic)   
 [Classe SoapFormatter](frlrfSystemRuntimeSerializationFormattersSoapSoapFormatterClassTopic)   
 [Classe Stream](frlrfSystemIOStreamClassTopic)   
 [Espace de noms System.IO](https://msdn.microsoft.com/en-us/library/system.io.aspx)   
 [Espace de noms System.Runtime.Serialization](frlrfSystemRuntimeSerialization)   
 [Espace de noms System.Xml.Serialization](frlrfSystemXmlSerialization)   
 [Sérialisation de base](../../../docs/framework/serialization/basic-serialization.md)   
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)   
 [Contrôle de la sérialisation XML à l'aide d'attributs](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [Sérialisation](../../../docs/framework/serialization/index.md)   
 [SOAP Service](http://msdn.microsoft.com/fr-fr/2051c992-28d1-499e-961f-17e9b675cec9)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)