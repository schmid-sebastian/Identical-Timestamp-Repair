# Identical-Timestamp-Repair
Process mining generates valuable insights into business processes through the analysis of event logs. However, event logs are commonly subject to various data quality issues which hinder the success of process mining initiatives in organizations. Identical timestamp errors, for example, occur when multiple events of a process instance mistakenly share the same timestamp. This error causes discovered process models to be unrepresentative and process performance analysis results to be misleading. To address this problem, we propose a method for automatically repairing identical timestamp errors in event logs. To that end, we combine existing method components for error detection and reordering of erroneous events with a novel approach for repairing timestamps based on Generative Adversarial Networks. 

## Chosen architecture
To account for the sequential nature of event data, we choose an LSTM-based GAN. An Illustration of the generator can be found below.

![generator_architecture](./Images/generator_architecture.png)

An Illustration of the generator can be found below.

![discriminator_architecture](./Images/discriminator_architecture.png)

## Results
We evaluated our approach by repairing six event logs in 30 different variations. We compare the performance of our approach against available baselines. The results for one exemplary real-life event log can be seen below.

![effectiveness_reordering](./Images/effectiveness_sorting.png)
![effectiveness_estimating](./Images/effectiveness_estimation.png)

## Requirements & Dependencies
We added a [requirements.txt](requirements.txt) as well as a [CycloneDX bill-of-material document](cyclonedx.xml) in the repository. 

## Usage
1.) Install the necessary libraries
> pip install -r requirements.txt
>
2.) Open TimestampGAN.ipynb, run the first cell and afterwards the following commands
>repair = TimestampGAN('path/to/event_log.csv', 'name_of_id_column', 'name_of_timestamp_column', 'name_of_activity_column', 'path/for/repaired/log/')
>
>repair.prepare_data()
>
>repair.reorder_events()
>
>repair.construct_networks()
>
>repair.train_gan()
>
>repair.repair_timestamps()
>
