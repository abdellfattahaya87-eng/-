/* =========================
   بتلات الورد
========================= */

const petals = document.getElementById("petals");

function createPetal(){

    const flower = document.createElement("img");

    flower.src = "petal.jpg";

    flower.className = "petal";

    flower.style.left = Math.random() * 100 + "vw";

    flower.style.animationDuration =
        (4 + Math.random() * 5) + "s";

    flower.style.width =
        (20 + Math.random() * 30) + "px";

    petals.appendChild(flower);

    setTimeout(() => {
        flower.remove();
    }, 9000);
}

setInterval(createPetal, 250);


/* =========================
   البوابة
========================= */

const gatePage = document.getElementById("gatePage");

const groom = document.querySelector(".groom");
const bride = document.querySelector(".bride");

groom.onclick = openGate;
bride.onclick = openGate;


function openGate(){

    /* إخفاء الصفحة الأولى */
    document.querySelector(".page")
        .classList.add("hidden");


    /* إظهار البوابة */
    gatePage.classList.remove("hidden");


    /* تشغيل الموسيقى */
    const music = document.getElementById("music");

    music.play().catch(() => {
        console.log("لم يتم تشغيل الموسيقى تلقائياً");
    });


    /* فتح البوابة */
    setTimeout(() => {

        document.getElementById("gateImage").src =
            "gateOpen.png";

    }, 1500);


    /* بدء الزوم */
    setTimeout(() => {

        document.getElementById("gateImage")
            .classList.add("zoomGate");

    }, 2500);


    /* الانتقال للدعوة */
    setTimeout(() => {

        gatePage.classList.add("hidden");

        const invite =
            document.getElementById("invitePage");

        invite.classList.remove("hidden");

        showInviteItems();

    }, 4500);

}


/* =========================
   تاريخ الزفاف
========================= */

const weddingDate =
    new Date("September 26, 2026 20:00:00").getTime();


function updateCountdown(){

    const now = new Date().getTime();

    const distance = weddingDate - now;


    /* لو وقت الفرح انتهى */
    if(distance <= 0){

        document.getElementById("days").innerHTML = "00";

        document.getElementById("hours").innerHTML = "00";

        document.getElementById("minutes").innerHTML = "00";

        document.getElementById("seconds").innerHTML = "00";

        return;
    }


    const days =
        Math.floor(
            distance /
            (1000 * 60 * 60 * 24)
        );


    const hours =
        Math.floor(
            (distance %
            (1000 * 60 * 60 * 24)) /
            (1000 * 60 * 60)
        );


    const minutes =
        Math.floor(
            (distance %
            (1000 * 60 * 60)) /
            (1000 * 60)
        );


    const seconds =
        Math.floor(
            (distance %
            (1000 * 60)) /
            1000
        );


    document.getElementById("days").innerHTML =
        String(days).padStart(2, "0");

    document.getElementById("hours").innerHTML =
        String(hours).padStart(2, "0");

    document.getElementById("minutes").innerHTML =
        String(minutes).padStart(2, "0");

    document.getElementById("seconds").innerHTML =
        String(seconds).padStart(2, "0");

}


updateCountdown();

setInterval(updateCountdown, 1000);


/* =========================
   صفحة التعليق
========================= */

function openComment(){

    document.getElementById("invitePage")
        .classList.add("hidden");


    document.getElementById("commentPage")
        .classList.remove("hidden");

}


/* =========================
   إرسال التعليق
========================= */

function sendComment(){

    const name =
        document.getElementById("guestName").value.trim();


    const attendBox =
        document.querySelector(
            'input[name="attend"]:checked'
        );


    const attend =
        attendBox ? attendBox.value : "";


    const message =
        document.getElementById("message").value.trim();


    /* التأكد من كتابة الاسم */
    if(name === ""){

        alert("من فضلك اكتب اسمك ❤️");

        return;
    }


    /* التأكد من اختيار الحضور */
    if(attend === ""){

        alert("من فضلك اختر إذا كنت ستحضر أم لا ❤️");

        return;
    }


    fetch(
        "https://script.google.com/macros/s/AKfycbxk3PF8ojhi-IRrFgXBg_S9xFLlM16ZUPsgg78dbs0gUynLDU00AamGetB77diZs0nIeA/exec",
        {
            method:"POST",

            body:JSON.stringify({

                name:name,

                attend:attend,

                message:message

            })
        }
    )

    .then(() => {

        alert("تم إرسال رسالتك بنجاح ❤️");


        /* إخفاء صفحة التعليق */

        document.getElementById("commentPage")
            .classList.add("hidden");


        /* العودة للدعوة */

        document.getElementById("invitePage")
            .classList.remove("hidden");


        /* تفريغ البيانات */

        document.getElementById("guestName").value = "";

        document.getElementById("message").value = "";

        const selected =
            document.querySelector(
                'input[name="attend"]:checked'
            );

        if(selected){
            selected.checked = false;
        }

    })

    .catch(() => {

        alert(
            "حدث خطأ أثناء إرسال الرسالة، حاول مرة أخرى ❤️"
        );

    });

}


/* =========================
   ظهور عناصر الدعوة
========================= */

function showInviteItems() {
    const items = document.querySelectorAll(".reveal");

    items.forEach((item, index) => {
        setTimeout(() => {
            item.classList.add("active");
        }, (index + 1) * 1200); // زيادة الوقت لـ 1.2 ثانية بين كل عنصر والتاني
    });
}
