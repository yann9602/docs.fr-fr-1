---
title: "Importation du sch&#233;ma pour g&#233;n&#233;rer des classes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, importation et exportation de schémas"
  - "Classe XsdDataContractImporter"
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Importation du sch&#233;ma pour g&#233;n&#233;rer des classes
Pour générer des classes à partir des schémas qui sont utilisables avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], utilisez la <xref:System.Runtime.Serialization.XsdDataContractImporter> (classe). Cette rubrique décrit le processus et les variations.  
  
## <a name="the-import-process"></a>Processus d'importation  
 Le processus d’importation de schéma démarre avec un <xref:System.Xml.Schema.XmlSchemaSet> et produit un <xref:System.CodeDom.CodeCompileUnit>.  
  
 Le `XmlSchemaSet` est une partie du modèle SOM (Schema Object Model) du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui représente un jeu de documents de schéma XSD (Schema Definition Language). Pour créer un `XmlSchemaSet` de l’objet à partir d’un ensemble de documents XSD, désérialisez chaque document dans un <xref:System.Xml.Schema.XmlSchema> objet (à l’aide de la <xref:System.Xml.Serialization.XmlSerializer>) et ajouter ces objets à un nouveau `XmlSchemaSet`.  
  
 Le `CodeCompileUnit` appartient au modèle CodeDOM (Code Document Object Model) du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui présente le code du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] de manière abstraite. Pour générer le code à partir d’un `CodeCompileUnit`, utilisez une sous-classe de la <xref:System.CodeDom.Compiler.CodeDomProvider> classe, telles que la <xref:Microsoft.CSharp.CSharpCodeProvider> ou <xref:Microsoft.VisualBasic.VBCodeProvider> classe.  
  
#### <a name="to-import-a-schema"></a>Pour importer un schéma  
  
1.  Créez une instance de la <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2.  Facultatif. Passez un `CodeCompileUnit` dans le constructeur. Les types générés pendant l'importation de schéma sont ajoutés à cette instance `CodeCompileUnit` au lieu de démarrer avec un `CodeCompileUnit` vide.  
  
3.  Facultatif. Appelez une de le <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> méthodes. La méthode détermine si le schéma donné est un schéma de contrat de données valide et peut être importé. La méthode `CanImport` a les mêmes surcharges que `Import` (étape suivante).  
  
4.  Appelez une des surchargées `Import` méthodes, par exemple, le <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> (méthode).  
  
     La surcharge la plus simple prend un `XmlSchemaSet` et importe tous les types, y compris les types anonymes figurant dans ce jeu de schémas. Autoriser les autres surcharges vous permettent de spécifier le type XSD ou une liste de types à importer (sous la forme d’un <xref:System.Xml.XmlQualifiedName> ou une collection de `XmlQualifiedName` objets). Dans ce cas, seuls les types spécifiés sont importés. Une surcharge prend un <xref:System.Xml.Schema.XmlSchemaElement> qui importe un élément particulier de le `XmlSchemaSet`, ainsi que son type associé (qu’il soit anonyme ou non). Cette surcharge retourne un `XmlQualifiedName` qui représente le nom de contrat de données du type généré pour cet élément.  
  
     Plusieurs appels de la méthode `Import` entraînent l'ajout de plusieurs éléments au même `CodeCompileUnit`. Un type n'est pas généré dans le `CodeCompileUnit` s'il est déjà présent. Appelez plusieurs fois `Import` sur le même `XsdDataContractImporter` au lieu d'utiliser plusieurs objets `XsdDataContractImporter`. Il s'agit de la méthode recommandée pour éviter de générer des types en double.  
  
    > [!NOTE]
    >  En cas de défaillance pendant l'importation, le `CodeCompileUnit` sera dans un état imprévisible. L'utilisation d'un `CodeCompileUnit` issu d'une importation ayant échoué pourrait vous exposer à des failles de sécurité.  
  
5.  Accès le `CodeCompileUnit` via la <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> propriété.  
  
### <a name="import-options-customizing-the-generated-types"></a>Option d'importation : personnalisation des types générés  
 Vous pouvez définir le <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriété de la <xref:System.Runtime.Serialization.XsdDataContractImporter> à une instance de la <xref:System.Runtime.Serialization.ImportOptions> classe de contrôler divers aspects du processus d’importation. Plusieurs options influencent directement les types générés.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Contrôle du niveau d'accès (GenerateInternal ou le commutateur /internal)  
 Cela correspond à la **/ interne** basculer le [Service Model Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Normalement, les types publics sont générés à partir d'un schéma, avec les champs privés et les propriétés de membres de données publiques correspondantes. Pour générer des types internes à la place, définissez les <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> propriété `true`.  
  
 L’exemple suivant montre un schéma transformé en interne classe lorsque les <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> est définie sur`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Contrôle des espaces de noms (espaces de noms ou le commutateur /namespace)  
 Cela correspond à la **/namespace** basculer le `Svcutil.exe` outil.  
  
 En règle générale, les types générés à partir du schéma sont générés dans [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] espaces de noms, avec chaque espace de noms XSD correspondant à un rôle particulier [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] espace de noms selon un mappage décrit dans [référence de schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Vous pouvez personnaliser ce mappage par le <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> propriété un <xref:System.Collections.Generic.Dictionary%602>.\</TKey, TValue> Si un espace de noms XSD donné figure dans le dictionnaire, l'espace de noms du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] correspondant est également issu de votre dictionnaire.  
  
 Par exemple, considérons le schéma suivant.  
  
 <!-- TODO: review snippet reference [!code[c_SchemaImportExport#10](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  -->  
  
 L'exemple suivant utilise la propriété `Namespaces` pour mapper l'espace de noms « http://schemas.contoso.com/carSchema » à « Contoso.Cars ».  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Ajout de SerializableAttribute (GenerateSerializable ou le commutateur /serializable)  
 Cela correspond à la **/ sérialisable** basculer le `Svcutil.exe` outil.  
  
 Parfois, il est important pour les types générés à partir du schéma soient utilisables avec [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] moteurs de sérialisation l’exécution (par exemple, le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=fullName> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> classes). Cela est utile lors de l'utilisation de types pour [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Remoting. Pour ce faire, vous devez appliquer le <xref:System.SerializableAttribute> aux types générés en plus de la mise à jour d’attribut <xref:System.Runtime.Serialization.DataContractAttribute> attribut. L'attribut est généré automatiquement si l'option d'importation `GenerateSerializable` a la valeur `true`.  
  
 L'exemple suivant affiche la classe `Vehicle` générée lorsque l'option d'importation `GenerateSerializable` a la valeur `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Ajout de la prise en charge de la liaisons de données (EnableDataBinding ou le commutateur /enableDataBinding)  
 Cela correspond à la **/enableDataBinding** basculer sur l’outil Svcutil.exe.  
  
 Il est parfois utile de lier les types générés à partir du schéma à des composants d'interface utilisateur graphique afin que toute mise à jour des instances de ces types mette à jour automatiquement l'interface utilisateur. Le `XsdDataContractImporter` peut générer des types qui implémentent la <xref:System.ComponentModel.INotifyPropertyChanged> interface de manière à ce que toute modification de propriété déclenche un événement. Si vous générez des types à utiliser avec un environnement de programmation de l’interface utilisateur client qui prend en charge cette interface (tel que [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)]), définissez les <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> propriété `true` pour activer cette fonctionnalité.  
  
 L’exemple suivant illustre la `Vehicle` classe générée avec le <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> la valeur `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Options d’importation : choix des types de collection  
 Deux modèles spéciaux au format XML représentent des collections d'éléments : les listes d'éléments et les associations entre un élément et un autre. Les éléments suivants sont un exemple d'une liste de chaînes.  
  
 <!-- TODO: review snippet reference [!code[C_SchemaImportExport#11](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  -->  
  
 Les éléments suivants sont un exemple d'une association entre une chaîne et un entier (`city name` et `population`).  
  
 <!-- TODO: review snippet reference [!code[C_SchemaImportExport#12](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  -->  
  
> [!NOTE]
>  Toute association peut aussi être considérée comme une liste. Par exemple, vous pouvez considérer l'association précédente comme une liste d'objets `city` complexes qui contiennent deux champs (un champ de chaîne et un champ d'entier). Les deux modèles sont représentés dans le schéma XSD. Il n'est pas possible de distinguer une liste et une association, donc ces modèles sont toujours traités comme des listes sauf si une annotation spéciale spécifique à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est présente dans le schéma. L’annotation indique qu’un modèle donné représente une association. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Référence du schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Normalement, une liste est importée sous la forme d'un contrat de données de collection qui dérive d'une liste générique ou sous la forme d'un tableau du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], selon si le schéma adopte ou non le modèle de désignation standard pour les collections. Cette opération est décrite plus en détail dans [des Types de collections dans les contrats de données](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Les associations sont importées normalement comme un <xref:System.Collections.Generic.Dictionary%602> ou d’un contrat de données de collection qui dérive de l’objet dictionary.\</TKey, TValue> Par exemple, considérons le schéma suivant.  
  
 <!-- TODO: review snippet reference [!code[c_SchemaImportExport#13](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  -->  
  
 Celui-ci serait importé comme suit (les champs sont montrés au lieu des propriétés à des fin de lisibilité).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Il est possible de personnaliser les types de collection générés pour ces modèles de schéma. Par exemple, vous souhaitez générer des collections dérivant de la <xref:System.ComponentModel.BindingList%601> au lieu de la <xref:System.Collections.Generic.List%601> classe afin de lier le type à une zone de liste et de mettre à jour le contenu de la collection est modifié. Pour ce faire, définissez la <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> propriétés de la <xref:System.Runtime.Serialization.ImportOptions> classe vers une liste de types de collection à utiliser (ci-après appelés les types référencés). Lors de l’importation d’une collection, cette liste de types de collection référencés est analysée et la collection qui correspond le mieux est utilisée, s’il en existe une. Les associations sont mappées uniquement aux types qui implémentent le type générique ou non générique <xref:System.Collections.IDictionary> interface, tandis que les listes sont mis en correspondance avec n’importe quel type de collection pris en charge.  
  
 Par exemple, si le <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> est définie sur une <xref:System.ComponentModel.BindingList%601>, le `people` type dans l’exemple précédent est généré comme suit.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Un type générique fermé est considéré comme la meilleure correspondance. Par exemple, si les types `BindingList(Of Integer)` et <xref:System.Collections.ArrayList> sont passés à la collection des types référencés, toutes les listes d’entiers présentes dans le schéma sont importées comme un `BindingList(Of Integer)`. Toutes les autres listes, par exemple `List(Of String)`, sont importées comme `ArrayList`.  
  
 Si un type qui implémente l'interface `IDictionary` générique est ajouté à la collection de types référencés, ses paramètres de type doivent être complètement ouverts ou complètement fermés.  
  
 Les doublons ne sont pas autorisés. Par exemple, vous ne pouvez pas ajouter à la fois `List(Of Integer)` et `Collection(Of Integer)` aux types référencés. Il serait alors impossible de déterminer lequel doit être utilisé lorsqu'une liste d'entiers est présente dans le schéma. Les doublons sont détectés uniquement si un type présent dans le schéma expose le problème des doublons. Par exemple, si le schéma importé ne contient pas de listes d'entiers, il est possible que la collection de types référencés contiennent à la fois `List(Of Integer)` et `Collection(Of Integer)`, mais aucun n'aura d'effet.  
  
 Le mécanisme des types de collection référencés fonctionne également bien pour les collections de types complexes (y compris les collections d'autres collections), et pas seulement pour les collections de primitives.  
  
 Le `ReferencedCollectionTypes` propriété correspond à la **/collectionType** basculer sur l’outil SvcUtil.exe. Notez que pour référencer plusieurs types de collection, le **/collectionType** commutateur doit être spécifié plusieurs fois. Si le type n’est pas dans le fichier MsCorLib.dll, son assembly doit être aussi référencé à l’aide de la **/reference** basculer.  
  
#### <a name="import-options-referencing-existing-types"></a>Options d'importation : référencement de types existants  
 Il arrive que des types dans le schéma correspondent à des types du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] existants et qu'il n'est pas nécessaire de générer ces types à partir de zéro. (Cette section s'applique uniquement aux types qui ne sont pas des collections. Pour les types de collection, consultez la section précédente.)  
  
 Par exemple, vous avez peut-être un type standard de contrat de données « Person » dans l'entreprise que vous souhaitez toujours utiliser pour représenter une personne. Chaque fois que certains services font appel à ce type, et que son schéma apparaît dans les métadonnées de service, vous pouvez réutiliser le type `Person` existant lorsque vous importez ce schéma au lieu d'en générer un nouveau pour chaque service.  
  
 Pour ce faire, passez une liste de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types que vous souhaitez réutiliser dans la collection le <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> propriété retourne sur le <xref:System.Runtime.Serialization.ImportOptions> classe. Si chacun de ces types a un nom et un espace de noms de contrat de données qui correspondent au nom et à l'espace de noms d'un type de schéma, une comparaison structurelle est effectuée. S'il est déterminé que les types ont à la fois des noms et des structures correspondants, le type du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] existant est réutilisé au lieu d'en générer un nouveau. Si seul le nom correspond mais pas la structure, une exception est levée. Notez qu'il n'y a aucune ressource pour le suivi des versions lors du référencement des types (par exemple, si vous ajoutez des membres de données facultatifs). Les structures doivent correspondre exactement.  
  
 Il est permis d'ajouter plusieurs types avec le même nom et espace de noms de contrat de données à la collection de types référencée, tant qu'aucun type de schéma n'est importé avec ce nom et cet espace de noms. Vous pouvez ainsi ajouter facilement tous les types dans un assembly à la collection sans tenir compte des doublons pour les types qui n’apparaissent pas réellement dans le schéma.  
  
 Le `ReferencedTypes` propriété correspond à la **/reference** basculer dans certains modes de fonctionnement de l’outil Svcutil.exe.  
  
> [!NOTE]
>  Lorsque vous utilisez Svcutil.exe ou (dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]) le **ajouter une référence de Service** outils, tous les types dans MsCorLib.dll sont référencés automatiquement.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Options d'importation : importer le schéma non DataContract comme types IXmlSerializable  
 Le <xref:System.Runtime.Serialization.XsdDataContractImporter> prend en charge un sous-ensemble limité du schéma. Si des constructions de schéma non prises en charge sont présentes (par exemple, les attributs XML), la tentative d'importation échoue et génère une exception. Cependant, la définition de la <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> propriété `true` étend la plage de schéma pris en charge. Lorsque la valeur `true`, le <xref:System.Runtime.Serialization.XsdDataContractImporter> génère des types qui implémentent la <xref:System.Xml.Serialization.IXmlSerializable> interface. Cette opération permet d'accéder directement à la représentation XML de ces types.  
  
##### <a name="design-considerations"></a>Considérations de design  
  
-   Il peut s'avérer difficile d'utiliser directement la représentation XML faiblement typée. Envisagez d’utiliser un moteur de sérialisation différent, tel que le <xref:System.Xml.Serialization.XmlSerializer>, pour utiliser les contrats schéma non compatible avec les données d’une manière fortement typée. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][À l’aide de la classe XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Certaines constructions de schéma ne peut pas être importées par le <xref:System.Runtime.Serialization.XsdDataContractImporter> même lorsque les <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> est définie sur `true`. Là encore, utilisez le <xref:System.Xml.Serialization.XmlSerializer> pour ces cas.  
  
-   Les constructions exactes de schéma qui sont pris en charge lors de la <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> est `true` ou `false` sont décrites dans [référence de schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Schéma généré <xref:System.Xml.Serialization.IXmlSerializable> types ne conservent pas le respect lorsque importés et exportés. Autrement dit, l'exportation du schéma à partir des types générés et son importation sous la forme de classes ne retournent pas le schéma d'origine.  
  
 Il est possible de combiner le <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> l’option avec la <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> option décrite précédemment. Pour les types qui doivent être générés en tant que <xref:System.Xml.Serialization.IXmlSerializable> implémentations, le contrôle structurel est ignoré lorsque vous utilisez la <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> fonctionnalité.  
  
 Le <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> option correspond à la **/importXmlTypes** basculer sur l’outil Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Utilisation des types IXmlSerializable générés  
 Le texte généré `IXmlSerializable` types contiennent un champ privé, nommé « nodesField », qui retourne un tableau de <xref:System.Xml.XmlNode> objets. Lorsque vous désérialisez une instance de ce type, vous pouvez accéder directement aux données XML par l'intermédiaire de ce champ en utilisant le modèle objet de document XML. Lorsque vous sérialisez une instance de ce type, vous pouvez affecter à ce champ les données XML souhaitées pour qu'il soit sérialisé.  
  
 Cette opération est possible grâce à l'implémentation `IXmlSerializable`. Dans le `IXmlSerializable` type, le <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implémentation appelle le <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> procédé de la <xref:System.Runtime.Serialization.XmlSerializableServices> (classe). La méthode est une méthode d’assistance qui convertit le code XML fournie par un <xref:System.Xml.XmlReader> vers un tableau de <xref:System.Xml.XmlNode> objets. Le <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> implémentation fait le contraire et convertit le tableau de `XmlNode` objets en une séquence de <xref:System.Xml.XmlWriter> appels. Cela est accompli en utilisant la <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> (méthode).  
  
 Il est possible d'exécuter le processus d'exportation de schéma sur les classes `IXmlSerializable` générées. Comme indiqué précédemment, le schéma d'origine n'est pas récupéré. À la place, vous obtiendrez le type XSD standard « anyType » qui est un caractère générique pour tout type XSD.  
  
 Cela en appliquant la <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> attribut généré `IXmlSerializable` classes et la spécification d’une méthode qui appelle le <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> méthode pour générer le type « anyType ».  
  
> [!NOTE]
>  Le <xref:System.Runtime.Serialization.XmlSerializableServices> type existe uniquement pour prendre en charge cette fonctionnalité particulière. Il n'est pas recommandé de l'utiliser à d'autres fins.  
  
#### <a name="import-options-advanced-options"></a>Options d'importation : options avancées  
 Les éléments suivants représentent les options d'importation avancées :  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> propriété. Spécifier la <xref:System.CodeDom.Compiler.CodeDomProvider> à utiliser pour générer le code pour les classes générées. Le mécanisme d’importation cherche à éviter les fonctionnalités que les <xref:System.CodeDom.Compiler.CodeDomProvider> ne prend pas en charge. Par exemple, le langage J# ne prend pas en charge de types génériques. Si vous spécifiez le fournisseur de code J# dans cette propriété, aucun type générique n’est générée dans l’importateur <xref:System.CodeDom.CodeCompileUnit>. Si le <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> n’est pas défini, l’ensemble des [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fonctionnalités est utilisé sans restrictions.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> propriété. Un <xref:System.Runtime.Serialization.IDataContractSurrogate> implémentation peut être spécifiée avec cette propriété. Le <xref:System.Runtime.Serialization.IDataContractSurrogate> personnalise le processus d’importation. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Substituts de contrat de données](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Par défaut, aucun substitut n'est utilisé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 <xref:System.Runtime.Serialization.ImportOptions>   
 [Référence de schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)   
 [Substituts de contrat de données](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)   
 [Exportation et importation de schéma](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)   
 [Exportation de schémas à partir de Classes](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)   
 [Référence de schéma de contrat de données](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)