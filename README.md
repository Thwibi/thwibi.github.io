<html lang="en"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Greetings</title>

    <style>


        body{
            font-variant-caps: all-petite-caps;


        }

        .widget {
            padding: 5px 5px ;
            color: #F7F7F7;
            display: flex;
            justify-content:center;
            align-items:center;
            flex-direction: column;
            max-width: 95%;
            margin: auto;
            border: 3px solid #F7F7F7;
            border-radius: 5px;
            box-shadow: 2px 2px 1px 0px #F7F7F7;

        }

           
        .greet{
            font-size: 3em;
        }

        .date {
      
            font-family: monospace;
            font-size: 2em;
        }

        .clock {
            font-family: monospace;
            font-size: 2em;
        }

        .time {
            display: inline-block;
            min-width: 20px;
        }

        .colon {
            font-size: 1em;
            display: inline-block;
        }

     




    </style>
</head>
<body>




<div class="container>">
    <div class="widget">

            <div class="greet" id="greet">Good Morning  </div>

                <div class="date" id="date">Thursday, June 22 2023</div>
                <div class="clock">
                    <div class="time" id="hour">07</div>
                    <div class="colon">:</div>
                    <div class="time" id="min">46</div>
                    <div class="colon">:</div>
                    <div class="time" id="sec">59 am</div>
                </div>
           

        

    </div>
</div>
        



<script>

function dispalyGreetings(today){
        hrs = today.getHours();
        name=""
        if (hrs < 12)
            greet = 'Good Morning  '+name;
        else if (hrs >= 12 && hrs <= 17)
            greet = 'Good Afternoon '+name;
        else if (hrs >= 17 && hrs <= 24)
            greet = 'Good Evening  '+name;
        document.getElementById('greet').innerHTML = greet;

    }

    function dispalyDate(today) {  
       
        const days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
        const monthNames = ["January", "February", "March", "April", "May", "June",
  "July", "August", "September", "October", "November", "December"
];

        var dayName = days[today.getDay()];
        var monthName = monthNames[today.getMonth()];
        var date = today.getDate();
        var year = today.getFullYear();
        document.getElementById('date').innerHTML =dayName+", "+monthName+" "+date+" "+year;

    }


    function dispalyClock(today) {

        var hour = padZeros(twelveHour(today.getHours()));
        var minutes = padZeros(today.getMinutes());
        var seconds = padZeros(today.getSeconds());
       
        if(today.getHours() >=12){
            seconds+=" pm"
        }
        else{
            seconds+=" am"
        }
       
        document.getElementById('hour').innerHTML = hour;
        document.getElementById('min').innerHTML = minutes;
        document.getElementById('sec').innerHTML = seconds;
    }

    function twelveHour(hour) {
        if (hour > 12) {
            return hour -= 12
        } else if (hour === 0) {
            return hour = 12;
        } else {
            return hour
        }
    }
    function padZeros(num) {
        if (num < 10) {
            num = '0' + num
        };
        return num;
    }

    function dispalyWidget() {
        var today = new Date();
        dispalyGreetings(today);
        dispalyDate(today);
        dispalyClock(today);
        setTimeout(dispalyWidget, 500);
    }

    dispalyWidget()

</script>


</body></html>
