# Tutorial 8

### How many data your publlsher program will send to the message broker in one run?

Program akan mengirim total 5 pesan data ke broker pesan dalam satu kali eksekusi. Setiap panggilan ke publish_event() mengirim satu pesan ke broker, dan terdapat 5 pemanggilan pada program utama.

### The url of: `amqp://guest:guest@localhost:5672` is the same as in the subscriber program, what does it mean?

Kedua program subscriber dan publisher menggunakan URL yang sama `amqp://guest:guest@localhost:5672`. Hal ini memastikan bahwa keduanya terhubung ke infrastruktur pesan yang sama yang disediakan oleh broker AMQP dan dapat bertukar pesan secara efektif.

## Running RabbitMQ as message broker

![Running RabbitMQ as message broker](images/image.png)

## Sending and processing event.

![Sending and processing event](images/image2.png)

Setelah menjalankan cargo run di publisher dan subscriber, maka Publisher akan mengirimkan data berupa 5 event ke broker yang diterima oleh Subscriber.

![Monitoring chart based on publisher](images/image3.png)

Spike dalam message rate terjadi karena program publisher dieksekusi berulang kali secara berurutan, mengirimkan sejumlah besar pesan ke broker pesan dalam waktu singkat. Seiring dengan bertambahnya jumlah pesan dalam queue, terjadi lonjakan tajam dalam message rate yang diterima oleh broker.