# Условия

Вы - распорядитель Главной Королевской Почты, в ваше ведомство поступают сообщения особой важности от агентов, и разведчиков, которые содержат разведданные и другие полезные сведения, которые используются при принятии решений в королевстве.

Однако в последнее время участились случаи, когда в ваше ведомство попадают ложные донесения от врагов, выдающих себя за агентов. Из-за таких донесений королевство принимает неверные решения, а там, глядишь, и до войны недалеко!

Работникам вашего ведомства удалось выбрать несколько сообщений, о которых доподлинно известно, что они были присланы вашими агентами и еще несколько сообщений, которые присланы, скорее всего, врагами. Ваша задача - тщательно их проанализировать, найти закономерности и разработать набор правил, по которым можно было бы определять, можно верить сообщению или нет.

Вашу работу будут оценивать очень строго: За каждое настоящее сообщение, которое пройдет проверку по вашим правилам, вы будете получать 3 балла, а за каждое ложное сообщение, которому удастся обмануть ваши правила, вас будут штрафовать на 2 балла. Чем больше правильных сообщений пройдет проверку и чем меньше ложных не пройдет, тем лучше!

Для удобства работы с сообщениями они были представлены в виде xml сообщений, а правила проверки подлинности должны быть оформлены в виде xsd схемы, по которой эти сообщения будут проверяться.

### Набор подлинных сообщений

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Andrew Levins</Agent>
        <Subject>North is under control</Subject>
        <PostalFee>80</PostalFee>
        <Region>
                <Kingdom>Mountain Hills</Kingdom>
        </Region>
        <Urgent>true</Urgent>
        <MessageCode>2</MessageCode>
        <Comment>Dear Queen! north of the kingdom is under conrtol.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Amanda Smith</Agent>
        <Subject>New gold minery established</Subject>
        <PostalFee>120</PostalFee>
        <Region>
                <Village>Shining Rocks</Village>
        </Region>
        <MessageCode>4</MessageCode>
        <Comment>Your Magesty! New gold minery was established at the Shining Rocks village.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Faceless Edward</Agent>
        <Subject>No news from the Iris Lake</Subject>
           <PostalFee>95</PostalFee>
        <Region>
                <Kingdom>Iris Lake</Kingdom>
        </Region>
        <MessageCode>7</MessageCode>
        <Urgent>false</Urgent>
        <Comment>Greetings, my Queen! No news is good news.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Richard Johnson</Agent>
        <Subject>People unhappy</Subject>
        <PostalFee>90</PostalFee>
        <Region>
                <Town>Thornwille</Town>
        </Region>
        <MessageCode>9</MessageCode>
        <Urgent>true</Urgent>
        <Comment>My Queen! Your attention needed to people of Thornwille.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Andrew Levins</Agent>
        <Subject>Something strange at the North-East</Subject>
        <PostalFee>100</PostalFee>
        <Region>
                <Kingdom>Mountain Hills</Kingdom>
        </Region>
        <MessageCode>4</MessageCode>
        <Urgent>true</Urgent>
        <Comment>Deer Queen! I recommend you to arrange scout squad to reveal activities at this Region.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Nickole</Agent>
        <Subject>No news from here</Subject>
        <PostalFee>80</PostalFee>
        <Region>
                <Village>Stillville</Village>
        </Region>
        <MessageCode>8</MessageCode>
        <Comment>My Queen! Everything is still in Stillville.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Amanda Smith</Agent>
        <Subject>Gold mining increased</Subject>
        <PostalFee>90</PostalFee>
        <Region>
                <Village>RichWoods</Village>
        </Region>
        <MessageCode>6</MessageCode>
        <Urgent>false</Urgent>
        <Comment>My Queen! Good news for you, our gold vallets would be fullfilled soon.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Frederick Pauls</Agent>
        <Subject>Half-Face King is planning attack!</Subject>
        <PostalFee>100</PostalFee>
        <Region>
                <Kingdom>ColdLakes</Kingdom>
        </Region>
        <MessageCode>4</MessageCode>
        <Urgent>true</Urgent>
        <Comment>Your Magesty! We need to defend our east.</Comment>
</Message>
~~~

### Набор ложных сообщений

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Peter Norton</Agent>
        <Subject>North is getting dangerous</Subject>
        <PostalFee>150</PostalFee>
        <Region>
                <Kingdom>Mountain Hills</Kingdom>
        </Region>
        <MessageCode>7</MessageCode>
        <Urgent>true</Urgent>
        <Comment>Dear Queen! north of the kingdom is getting dangerous!</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Miranda Smith</Agent>
        <Subject>New gold minery exploded</Subject>
        <PostalFee>120</PostalFee>
        <Region>
                   <City>Sparkling Castle</City>
        </Region>
        <MessageCode>9</MessageCode>
        <Comment>Your Magesty! We need additional supply, our midery dosn't work any more.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Faceless Edward</Agent>
        <Subject>No news from the Beawers Lake</Subject>
        <PostalFee>0</PostalFee>
        <Region>
                <Kingdom>Iris Lake</Kingdom>
        </Region>
        <MessageCode>16</MessageCode>
        <Comment>Greetings, my Queen! No news from Beawers Lake.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Richard Johnson</Agent>
        <Subject>People are happy</Subject>
        <PostalFee>90</PostalFee>
        <Region>
                <Town>Thornwille</Town>
        </Region>
        <MessageCode>9</MessageCode>
        <Urgent>no</Urgent>
        <Comment>My Queen! Your attention is not needed here.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Sir Andrew Levins</Agent>
        <Subject>Something strange at the North-West</Subject>
        <Region>
                <Kingdom>Mountain Hills</Kingdom>
        </Region>
        <MessageCode>4</MessageCode>
        <Urgent>true</Urgent>
        <Comment>Deer Queen! I recommend you to arrange scout squad to
reveal activities at this Region.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Nickole</Agent>
        <Subject>No news from here</Subject>
	<PostalFee>80</PostalFee>
        <Village>Stillville</Village>
        <MessageCode>8</MessageCode>
        <Comment>My Queen! Everything is still in Stillville.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Amanda Smith</Agent>
        <Subject>Gold mining decreased</Subject>
        <PostalFee>90</PostalFee>
        <Region>
                <Village>RichWoods</Village>
        </Region>
        <MessageCode>6</MessageCode>
        <Urgent>false</Urgent>
        <Code>4</Code>
        <Comment>My Queen! Bad news for you, our gold vallets would be empty soon.</Comment>
</Message>
~~~

~~~
<?xml version='1.0' encoding='UTF-8'?>
<Message>
        <Agent>Frederick Pauls</Agent>
        <Subject>Red King is planning attack!</Subject>
        <PostalFee>100</PostalFee>
        <Region>
                <Kingdom>ColdLakes</Kingdom>
        </Region>
        <MessageCode>4</MessageCode>
        <Urgent>true</Urgent>
        <Comment>We need to attack Red King first.</Comment>
</Message>
~~~

### Как оформить решение

В задании приведено два набора по 8 xml сообщений.

Вам необходимо сформировать и загрузить на сервер xsd схему, по которой будут проверяться все сообщения по очереди. Схема должна быть составлена таким образом, чтобы как можно больше сообщений из первого блока проходили проверку по ней и как можно больше сообщений из второго блока - не проходили.
