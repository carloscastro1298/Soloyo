const header = document.querySelector("header");
const cards = document.querySelectorAll(".card");

window.addEventListener("scroll", () => {
    if(window.scrollY > 50){
        header.classList.add("scrolled");
    } else {
        header.classList.remove("scrolled");
    }
});

const observer = new IntersectionObserver((entries)=>{
    entries.forEach(entry=>{
        if(entry.isIntersecting){
            entry.target.classList.add("visible");
        }
    });
},{
    threshold:0.3
});

cards.forEach(card=>{
    observer.observe(card);
});

document.addEventListener("mousemove",(e)=>{
    let x = e.clientX / window.innerWidth;
    let y = e.clientY / window.innerHeight;

    document.body.style.background = `linear-gradient(
        ${x*360}deg,
        #1e1e2f,
        #2b2b45,
        #3a3a60
    )`;
});
