📌 About the Project

Pasid-Validator with autoscaling support is an open-source tool developed to validate models based on Stochastic Petri Nets (SPN). It allows comparing the behavior of a theoretical model with real experiments through statistical metrics, with emphasis on the mean response time (MRT).

This repository contains the extended version of the tool, with support for dynamic autoscaling logic, implemented and validated in the context of Vehicular Networks (VANETs).

🧪 Features
º Statistical validation of SPN models with real experiments;
º Full support for service autoscaling logic with reinstantiation;
º Automatic collection of intermediate execution times;
º Generation of models based on experimental times;
º Execution of t-tests to compare model and reality;
º Generation of validation graphs and metrics.

🗂 Project Structure
bash
Copy
Edit
Pasid_Validador_Autoscaling/
├── deploy/ # Versão empacotada para execução distribuída
├── lib/ # Biblioteca mercuryauto.jar
├── src/ # Código-fonte principal
│ └── tests/
│ ├── model/ # Modelo SPN e simulação via MercuryCall_Services
│ └── validation/ # Execução experimental e comparação
├── graphs_services/ # Saída gráfica da simulação
├── resources/ # Arquivos .properties de configuração
└── pom.xml # Arquivo de build do Maven

Link to the base Pasid-Validator tutorial: https://docs.google.com/document/d/1EMwqjL4nJPaaYRZAEW5e5JSSK-D_aH1P1fUSUC5c7GI/edit?tab=t.0

⚙️ Installation and Configuration
✅ Prerequisites
Java 11 (recommended: Zulu JDK)

Windows

Linux

Mercuryauto.jar

Maven to build the project

▶️ Installation Steps
Install Java and configure it in the project via:

Copy
Edit
File > Project Structure > Project
Place mercuryauto.jar in the lib/ folder and add it as a library to the project.

Build with Maven:

bash
Copy
Edit
mvn clean install
🧪 Running Validation
Validation is done in 4 main steps:

1. Experimental Collection (Feeding)
   java
   Copy
   Edit
   modelFeedingStage = true
   Run LocalTest_Services to obtain intermediate times (T1, T2, ..., Tn).

2. SPN Model Simulation
   Run MercuryCall_Services with the times obtained in the previous step. The results (MRTs) will be saved in source.properties.

3. Experimental Execution with Autoscaling
   Run LocalTest_Services again, now varying the parameters (such as number of services). Autoscaling will be activated automatically based on queue occupancy (>80%).

4. Comparison of Results
   The tool automatically runs the t-test and displays the result of the statistical adherence between the model and the real experiment.

📊 Scientific Validation
The Pasid-Validator with autoscaling support was used in Case Study 3 of the cited article, where it was validated with real data, presenting high statistical adherence (p-value > 0.05 and t ~ 0). The simulated MRT remained within the 95% confidence interval for all scenarios analyzed.

The tool proved to be capable of faithfully reproducing the adaptive dynamics of container instantiation and reinstantiation, being especially useful for validating SPN models of elastic vehicular infrastructure.
