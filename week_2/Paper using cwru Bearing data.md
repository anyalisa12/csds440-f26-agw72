 Federated Learning for Privacy-Preserving Collaboration- Jianjing 
This paper uses the data set I will be using for my study.

Federated Learning for Privacy-Preserving
Collaboration in Smart Manufacturing
Jianjing Zhang1

, Clayton Cooper1 and Robert X. Gao1*
1 Case Western Reserve University, Cleveland, OH 44106, USA
* Corresponding author. Tel.: +01 (216) 368-6045. E-mail address: Robert.Gao@case.edu

Abstract. Manufacturing has entered the era of digital transformation in which

manufacturers are increasingly connected as part of a broad-based smart and con-
nected community. This transformation, enabled by artificial intelligence (AI),

offers great potential to deepen the collaboration among manufacturers through
resource and knowledge sharing, which in turn contributes to the sustainability
of manufacturing. While the benefits of AI have been increasingly demonstrated,

one major hurdle towards collaborative data-driven modeling for enhancing man-
ufacturing is the concern about data privacy. As a result, rich information embed-
ded in manufacturing data collected by individual manufacturers is typically si-
loed within the bounds of the data owners and is thus under-utilized. This paper

describes an approach to tackling this challenge using federated learning, where
each data owner contributes to the creation of a comprehensive, global data
model by computing a local update of relevant model parameters based on its
own data. The local updates are then aggregated by a central server to train a
global model. Since only the model parameters instead of the data are shared

across the various data owners, data-privacy is preserved. Evaluation using sen-
sor data acquired for machine condition monitoring as a representative manufac-
turing application has shown that federated learning is successful in producing a

global model that is more accurate and robust than each of the local models es-
tablished by each single data owner. The result demonstrates the benefit of secure

information sharing for individual manufacturers, especially Small and Mid-
Sized Manufacturers (SMMs), for improved sustainable operation.

Keywords: Smart manufacturing, Federated learning, Data privacy.
1 Introduction
Smart and connected technologies, such as multimodal sensing, Internet of Things
(IoT), and artificial intelligence (AI), have demonstrated potential in transforming the
landscape of manufacturing toward improved productivity and the overall well-being
of the community in which manufacturers reside [1]. However, for many Small and

Mid-Sized Manufacturers (SMMs), digital transformation presents a significant chal-
lenge due to the general lack of resources to support technology adoption. These factors

negatively impact SMMs in their competitiveness for digitalization as the future of
manufacturing calls for, reducing their resilience to machine performance fluctuation
and supply chain disruptions, and affecting the pipeline for workforce training, talent
