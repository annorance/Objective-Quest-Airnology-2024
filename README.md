# Objective-Quest-Airnology-2024
## Description
In today’s digital era, cybersecurity has become one of the top priorities for companies managing high-traffic websites. As the number of users and connected devices increases, along with the growing complexity of cyberattacks, the need to monitor and protect networks becomes even more crucial. Every day, large companies must handle various types of traffic flowing in and out of their servers—from legitimate user activity to potential threats such as attacks and other malicious behavior.

To maintain network integrity and security, cybersecurity teams must effectively identify and classify the types of traffic within the network. However, with massive data volumes and high variability in traffic patterns, a system capable of real-time detection and analysis of suspicious activity is required. Building an effective model will enable companies to proactively detect and respond to potential threats.

## Task
Participants are expected to build and develop a predictive model that can classify network traffic types. This model must be able to analyze large and diverse traffic data, identify suspicious patterns, and accurately predict the traffic category.

Jenis-jenis Traffic yang Harus Diprediksi:
- Background – Routine or background traffic that typically does not pose a threat.
- Benign – Traffic that shows no signs of harmful or anomalous activity.
- Probing – Scanning or probing activity to identify vulnerabilities or targets.
- Bruteforce – Attack attempts using various password combinations to gain access.
- XMRIGCC CryptoMiner – Activities related to covert cryptocurrency mining.
- Bruteforce-XML – Brute force attacks targeting XML-based applications.

## Evaluation Metric
In this competition, model performance will be evaluated using the average of the Balanced Accuracy Score and Accuracy Score.
```
from sklearn.metrics import accuracy_score, balanced_accuracy_score

bal_acc = balanced_accuracy_score(solution, submission)
acc = accuracy_score(solution, submission)
score = (bal_acc+acc)/2
```
The final score (100%) is based on the leaderboard, which reflects the accuracy consistency between the organizer’s notebook validation and the participant’s Kaggle submission. The final score will be calculated using a weighted average:
```
nilai akhir = 30% public + 70% private
```

## Dataset
### Files
- `train.csv` - log of network activity and traffic used for training the model.
- `test.csv` - log of network activity and traffic to be predicted.
- `sample_submission.csv` - sample submission format.
### Features
- id - Unique ID for each network flow
- origin_host - IP address of the client
- origin_port - Port number used by the client
- response_host - IP address of the server
- response_port - Port number used by the server
- flow_duration - Duration of the network flow
- forward_packets_per_sec - Rate of packet transmission from client to server per second
- backward_packets_per_sec - Rate of packet transmission from server to client per second
- flow_packets_per_sec - Total packet rate in the entire flow
- down_up_ratio - Ratio of downloaded to uploaded bytes or packets
- flow_FIN_flags - Number of FIN flags indicating the end of a TCP connection
- flow_SYN_flags - Number of SYN flags used to initiate a TCP connection
- flow_RST_flags - Number of RST flags indicating a TCP connection reset
- forward_PSH_flags - PSH flags indicating data that must be processed immediately by the server
- backward_PSH_flags - PSH flags indicating data that must be processed immediately by the client
- flow_ACK_flags - ACK flags used to confirm receipt of packets
- forward_URG_flags - URG flags indicating urgent data from the client
- backward_URG_flags - URG flags indicating urgent data from the server
- flow_CWR_flags - CWR flags indicating reduced congestion window size
- flow_ECE_flags - ECE flags indicating network congestion
- forward_pkts_payload - Average payload size in packets from client to server
- backward_pkts_payload - Average payload size in packets from server to client
- flow_pkts_payload - Average payload size across the entire flow
- forward_iat - Average Inter Arrival Time (IAT) between packets from client to server
- backward_iat - Average IAT between packets from server to client
- flow_iat - Average IAT in the entire flow
- payload_bytes_per_sec - Payload transfer rate per second
- forward_subflow_packets - Number of packets in the client-to-server subflow
- backward_subflow_packets - Number of packets in the server-to-client subflow
- forward_subflow_bytes - Number of bytes in the client-to-server subflow
- backward_subflow_bytes - Number of bytes in the server-to-client subflow
- forward_bulk_bytes - Number of bulk bytes from client to server
- backward_bulk_bytes - Number of bulk bytes from server to client
- forward_bulk_packets - Number of bulk packets from client to server
- backward_bulk_packets - Number of bulk packets from server to client
- forward_bulk_rate - Bulk traffic rate from client to server
- backward_bulk_rate - Bulk traffic rate from server to client
- active - Average active time during which data is transmitted
- idle - Average idle time during which no data is transmitted
- forward_initial_window_size - Initial flow control window size from client to server
- backward_initial_window_size - Initial flow control window size from server to client
- forward_last_window_size - Final window size from client to server
### Target
Traffic:
- Background
- Benign
- Probing
- Bruteforce
- XMRIGCC CryptoMinerBruteforce-XML

## Result and Discussion
To address class imbalance in the dataset, the BorderlineSMOTE technique was applied—an oversampling method that focuses on generating synthetic data near decision boundaries between classes. The model used was Multilayer Perceptron Classifier (MLPClassifier) with a three-hidden-layer architecture containing 150, 100, and 50 neurons respectively. The model was configured with the ReLU activation function, optimized using Adam, and used a ridge penalty (alpha) of 0.01. The batch size was set to 400, initial learning rate to 0.001, maximum iterations to 5000, and convergence tolerance to 1e-6 for more stable optimization.

Evaluation results showed strong performance, with a public score of 0.73250 and a private score of 0.73547. The relatively small difference between public and private scores indicates good generalization ability of the model on unseen data. Additionally, the use of BorderlineSMOTE proved effective in improving model performance on the imbalanced dataset.

## Citation 
Arkan Attaqy, Elzandi Irfan Zikra, GATOT, Lemuel Horas, miaw🐟, and Zys. Objective Quest Dataquest 2024. https://kaggle.com/competitions/objective-quest-dataquest, 2024. Kaggle.

## Competition Link
https://www.kaggle.com/competitions/objective-quest-dataquest
