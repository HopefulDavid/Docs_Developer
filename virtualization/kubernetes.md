> [!IMPORTANT]
> Je zapotřebí znalost dockeru

> [!NOTE]
> - Dovedete si představit, jak obtížné je spravovat kontejnery, které mohou běžet i na stovkách serverů? 
>
> 	Manuálně je to nad lidské síly, a proto se ke správě využívají **orchestrátory**.
> 
> - Je jedním z několika softwarových orchestrátorů. 

Software nad kontejnerovou sítí, automaticky se stará o zavádění, údržbu a škálování kontejnerizovaných aplikací.

V praxi umožňují efektivně využívat kapacitu serverů, reagují na podněty a dynamicky služby spouští, vypínají staré verze a zapínají nové apod. 

- Ukázka orchestrátoru:

	<img src="https://www.master.cz/mydata/myuploads/2020/08/kontejnery2.png" alt="Kubernetes_kontejnery"/>

    > [!NOTE]
    > Orchestrátory usnadnily práci především vývojářům microservices.

    - Microservices 
    
      Způsob vývoje a provozování aplikací rozdělených na menší moduly, které spolu komunikují prostřednictvím API. 
    
      Na rozdíl od velkých monolitických aplikací, jsou microservices snadné na údržbu, protože změna v jednom modulu se neprojeví v ostatních částech.

## Vysvětlení

<iframe width="560" height="315" src="https://www.youtube.com/embed/aSrqRSk43lY?si=qyuGFC3OLJ_knERz" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

- 0:00 - 00:28 - Úvod
- 0:28 - 01:55 - Komponenty
- 1:55 - 04:07 - Nasazení aplikace přes Pod 
- 4:07 - 07:09 - Standardní nasazení aplikace
- 07:09 - 09:16 - Registry služeb pro správu a komunikaci aplikací uvnitř kubernetes
- 09:16 - 10:13 - Zveřejnění přístupu do aplikace z kubernetes

## Video přednáška

<video src="https://download.wug.cz/videos/wug/WUGBrno_WUG-Days-2022_Migrace-stavajicich-aplikaci-do-Kubernetes/WUGBrno_WUG-Days-2022_Migrace-stavajicich-aplikaci-do-Kubernetes_HD.mp4" alt="WUGBrno_WUG-Days-2022_Migrace-stavajicich-aplikaci-do-Kubernetes_HD.mp4" width="800px"/>

[Zdroj](https://www.master.cz/blog/docker-kubernetes-kontejnery-jak-funguji-proc-je-chtit/)