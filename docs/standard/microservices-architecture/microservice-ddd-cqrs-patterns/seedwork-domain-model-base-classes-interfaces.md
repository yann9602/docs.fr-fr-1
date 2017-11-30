---
title: "Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="83d0f-104">Seedwork (classes de base réutilisables et interfaces pour votre modèle de domaine)</span><span class="sxs-lookup"><span data-stu-id="83d0f-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="83d0f-105">Le dossier de solution contient un *SeedWork* dossier.</span><span class="sxs-lookup"><span data-stu-id="83d0f-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="83d0f-106">Le *SeedWork* dossier contient des classes de base personnalisées que vous pouvez utiliser comme base pour vos entités de domaine et les objets de valeur.</span><span class="sxs-lookup"><span data-stu-id="83d0f-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="83d0f-107">Utilisez ces classes de base, donc vous n’avez pas de code redondant dans la classe d’objet de chaque domaine.</span><span class="sxs-lookup"><span data-stu-id="83d0f-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="83d0f-108">Le dossier pour ces types de classes est appelé *SeedWork* et pas quelque chose comme *Framework*.</span><span class="sxs-lookup"><span data-stu-id="83d0f-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="83d0f-109">Il est appelé *SeedWork* , car le dossier contient un sous-ensemble des classes réutilisables qui ne peut pas réellement être considérée comme une infrastructure.</span><span class="sxs-lookup"><span data-stu-id="83d0f-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="83d0f-110">*Seedwork* est un terme introduit par [Michael plumes](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) déjà connues par [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) , mais vous pouvez également nommer ce dossier commun, SharedKernel, ou similaires.</span><span class="sxs-lookup"><span data-stu-id="83d0f-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="83d0f-111">Figure 9-12 montre les classes qui constituent le seedwork du modèle de domaine dans l’ordre de tri microservice.</span><span class="sxs-lookup"><span data-stu-id="83d0f-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="83d0f-112">Il a quelques classes de base personnalisées comme entité, ValueObject et d’énumération, ainsi que quelques interfaces.</span><span class="sxs-lookup"><span data-stu-id="83d0f-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="83d0f-113">Ces interfaces (IRepository et IUnitOfWork) informent la couche d’infrastructure sur ce qui doit être implémentée.</span><span class="sxs-lookup"><span data-stu-id="83d0f-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="83d0f-114">Ces interfaces sont également utilisés par le biais d’Injection de dépendance à partir de la couche application.</span><span class="sxs-lookup"><span data-stu-id="83d0f-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="83d0f-115">**Figure 9-12**.</span><span class="sxs-lookup"><span data-stu-id="83d0f-115">**Figure 9-12**.</span></span> <span data-ttu-id="83d0f-116">Un exemple de définie des classes de base de domaine modèle « seedwork » et des interfaces</span><span class="sxs-lookup"><span data-stu-id="83d0f-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="83d0f-117">Il s’agit du type de réutilisation de copier- coller de nombreux développeurs partagent entre les projets, pas un cadre formel.</span><span class="sxs-lookup"><span data-stu-id="83d0f-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="83d0f-118">Vous pouvez avoir seedworks dans n’importe quel couche ou la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="83d0f-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="83d0f-119">Toutefois, si l’ensemble des classes et interfaces est suffisante, vous souhaiterez créer une bibliothèque de classes unique.</span><span class="sxs-lookup"><span data-stu-id="83d0f-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="83d0f-120">La classe de base d’entité personnalisée</span><span class="sxs-lookup"><span data-stu-id="83d0f-120">The custom Entity base class</span></span>

<span data-ttu-id="83d0f-121">Le code suivant est un exemple d’une classe de base d’entité dans lequel vous pouvez placer le code qui peut être utilisé de la même façon par une entité de domaine, tels que l’ID d’entité, [opérateurs d’égalité](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc..</span><span class="sxs-lookup"><span data-stu-id="83d0f-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }
  
    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }

    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }

    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="83d0f-122">Contrats de référentiel (interfaces) dans la couche de modèle de domaine</span><span class="sxs-lookup"><span data-stu-id="83d0f-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="83d0f-123">Contrats de référentiel sont simplement des interfaces .NET qui expriment les spécifications de contrat des espaces de stockage à utiliser pour chaque agrégat.</span><span class="sxs-lookup"><span data-stu-id="83d0f-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> <span data-ttu-id="83d0f-124">Les référentiels eux-mêmes, avec le code d’une base de EF ou d’autres dépendances d’infrastructure et le code, ne doivent pas être implémentées dans le modèle de domaine ; les référentiels doivent uniquement implémenter les interfaces que vous définissez.</span><span class="sxs-lookup"><span data-stu-id="83d0f-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code, must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span>

<span data-ttu-id="83d0f-125">Un modèle lié à cette pratique (en plaçant les interfaces de référentiel dans la couche de modèle de domaine) est un modèle séparées par une Interface.</span><span class="sxs-lookup"><span data-stu-id="83d0f-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="83d0f-126">En tant que [expliqué](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) par Martin Fowler, « utilisation séparées par Interface pour définir une interface dans un package mais l’implémenter dans un autre.</span><span class="sxs-lookup"><span data-stu-id="83d0f-126">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="83d0f-127">De cette manière un client qui a besoin de la dépendance à l’interface peut être pas tenu au courant de l’implémentation. »</span><span class="sxs-lookup"><span data-stu-id="83d0f-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="83d0f-128">Suivant le modèle séparées par une Interface permet à la couche d’application (dans ce cas, le projet d’API Web pour le microservice) pour avoir une dépendance sur les exigences définies dans le modèle de domaine, mais pas une dépendance directe à l’infrastructure/persistance couche.</span><span class="sxs-lookup"><span data-stu-id="83d0f-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="83d0f-129">En outre, vous pouvez utiliser l’Injection de dépendances pour isoler l’implémentation, qui est implémentée dans l’infrastructure / de la couche de persistance à l’aide de référentiels.</span><span class="sxs-lookup"><span data-stu-id="83d0f-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="83d0f-130">Par exemple, l’exemple suivant, avec l’interface IOrderRepository définit les opérations de la classe OrderRepository doit implémenter à la couche d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="83d0f-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="83d0f-131">Dans l’implémentation actuelle de l’application, le code doit simplement ajouter l’ordre de la base de données, étant donné que les requêtes sont les suivants de fractionner que l’approche CQS et les mises à jour des commandes ne sont pas implémentées.</span><span class="sxs-lookup"><span data-stu-id="83d0f-131">In the current implementation of the application, the code just needs to add the order to the database, since queries are split following the CQS approach, and updates to orders are not implemented.</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="83d0f-132">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="83d0f-132">Additional resources</span></span>

-   <span data-ttu-id="83d0f-133">**Martin Fowler. Interface séparé. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="83d0f-133">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="83d0f-134">[Précédente] (net-core-microservice-domaine-model.md) [suivant] (implémentez-valeur objects.md)</span><span class="sxs-lookup"><span data-stu-id="83d0f-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
