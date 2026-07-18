<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>50 Wild Wonders </title>

    <!-- ===== AUDIO ===== -->
    <!-- YouTube embed for "So Into You" by Tamia (autoplay, loop, muted not set) -->
    <!-- We'll use an iframe with autoplay & loop. Volume is controlled by the user's system. -->
    <!-- To make it autoplay, we use a small trick: an invisible iframe with autoplay. -->
    <!-- Modern browsers require user interaction, so we'll also add a small visible play button. -->

    <style>
        /* ----- RESET ----- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0b0b0b;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            font-family: 'Georgia', 'Times New Roman', serif;
            padding: 20px;
        }

        /* ----- TOP TITLE ----- */
        .main-title {
            font-size: clamp(2.8rem, 10vw, 6rem);
            font-weight: 300;
            letter-spacing: 6px;
            color: #f5e6d3;
            text-shadow: 0 0 30px rgba(255, 215, 180, 0.2);
            margin-top: 20px;
            margin-bottom: 30px;
            text-align: center;
            font-style: italic;
            border-bottom: 1px solid rgba(255, 215, 180, 0.15);
            padding-bottom: 15px;
            width: 80%;
            max-width: 800px;
        }

        /* ----- SLIDESHOW CONTAINER ----- */
        .slideshow-container {
            position: relative;
            width: 100%;
            max-width: 900px;
            background: #1a1a1a;
            border-radius: 24px;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.8);
            border: 1px solid rgba(255, 215, 180, 0.1);
        }

        /* ----- SLIDE ----- */
        .slide {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 30px 20px 40px;
            min-height: 500px;
            animation: fade 1s ease-in-out;
        }

        .slide.active {
            display: flex;
        }

        @keyframes fade {
            0% { opacity: 0.3; }
            100% { opacity: 1; }
        }

        .slide img {
            width: 100%;
            max-width: 700px;
            max-height: 420px;
            object-fit: cover;
            border-radius: 16px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.6);
            border: 1px solid rgba(255, 255, 255, 0.05);
            background: #2a2a2a;
        }

        .bird-name {
            font-size: clamp(1.8rem, 4vw, 2.8rem);
            color: #f0dcc8;
            margin-top: 22px;
            font-weight: 400;
            letter-spacing: 2px;
            text-shadow: 0 0 20px rgba(255, 200, 150, 0.15);
        }

        .bird-fact {
            font-size: clamp(1rem, 1.5vw, 1.2rem);
            color: #b8a99a;
            margin-top: 8px;
            max-width: 650px;
            text-align: center;
            line-height: 1.6;
            font-style: italic;
            padding: 0 10px;
        }

        /* ----- DOTS / INDICATORS ----- */
        .dots-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 8px;
            padding: 18px 12px 12px;
            background: rgba(0, 0, 0, 0.4);
        }

        .dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: #4a3f38;
            transition: background 0.3s;
            cursor: pointer;
        }

        .dot.active {
            background: #e8c9ae;
            box-shadow: 0 0 12px rgba(232, 201, 174, 0.4);
        }

        /* ----- BOTTOM SIGNATURE ----- */
        .signature {
            font-size: clamp(1.2rem, 2vw, 1.8rem);
            color: #cbb5a2;
            margin-top: 30px;
            margin-bottom: 20px;
            letter-spacing: 3px;
            font-weight: 300;
            text-align: center;
            border-top: 1px solid rgba(255, 215, 180, 0.1);
            padding-top: 25px;
            width: 70%;
            max-width: 600px;
            font-style: italic;
        }

        /* ----- AUDIO PLAY BUTTON (simple, elegant) ----- */
        .audio-btn {
            background: none;
            border: 1px solid rgba(255, 215, 180, 0.25);
            color: #d4c0b0;
            padding: 10px 24px;
            border-radius: 40px;
            font-size: 0.9rem;
            font-family: 'Georgia', serif;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
            background: rgba(255, 215, 180, 0.05);
            letter-spacing: 1px;
        }

        .audio-btn:hover {
            background: rgba(255, 215, 180, 0.12);
            border-color: rgba(255, 215, 180, 0.5);
            color: #f0dcc8;
        }

        .audio-btn.playing {
            border-color: #e8c9ae;
            color: #e8c9ae;
            box-shadow: 0 0 20px rgba(232, 201, 174, 0.15);
        }

        /* responsive */
        @media (max-width: 600px) {
            .slide {
                min-height: 350px;
                padding: 15px 10px 25px;
            }
            .slide img {
                max-height: 240px;
            }
            .dots-container {
                gap: 5px;
                padding: 12px 8px 8px;
            }
            .dot {
                width: 7px;
                height: 7px;
            }
        }
    </style>
</head>
<body>

    <!-- ===== TOP TITLE ===== -->
    <div class="main-title">50 Wild Wonders</div>

    <!-- ===== SLIDESHOW ===== -->
    <div class="slideshow-container">
        <div id="slidesWrapper">
            <!-- slides will be injected by JS -->
        </div>
        <div class="dots-container" id="dotsContainer"></div>
    </div>

    <!-- ===== SIGNATURE ===== -->
    <div class="signature">I love you Mrs. Fredrickson</div>

    <!-- ===== AUDIO BUTTON ===== -->
    <button class="audio-btn" id="audioBtn">🎵 Play "So Into You"</button>

    <!-- Hidden YouTube iframe for audio -->
    <div id="youtubeAudio" style="display:none;"></div>

    <script>
        // ============================================================
        // 1. BIRD DATA – 50 species with facts
        // ============================================================
        const birds = [
            { name: "Lilac-breasted Roller", fact: "Botswana's national bird. Its feathers shimmer with eight different colors in sunlight." },
            { name: "African Fish Eagle", fact: "Its distinctive call is known as the 'voice of Africa.' They mate for life." },
            { name: "Southern Ground Hornbill", fact: "They live in family groups of up to 10 birds and cooperate to raise chicks." },
            { name: "Secretary Bird", fact: "Stomps on snakes with powerful legs. Its name comes from the quill-like feathers behind its head." },
            { name: "Barn Owl", fact: "Can hunt in complete darkness using only sound — its hearing is among the best in the animal kingdom." },
            { name: "Kingfisher", fact: "Dives into water at high speed to catch fish. Its eyes adjust instantly underwater." },
            { name: "Crimson Sunbird", fact: "The male's bright red feathers are so vivid they appear to glow in direct sunlight." },
            { name: "African Paradise Flycatcher", fact: "The male grows long tail streamers that can be twice the length of its body." },
            { name: "Helmeted Guineafowl", fact: "Has a bony casque on its head. They run on the ground and fly only short distances." },
            { name: "Kori Bustard", fact: "The heaviest flying bird in Africa — males can weigh up to 18 kg (40 lbs)." },
            { name: "Marabou Stork", fact: "Called the 'undertaker bird' due to its dark cloak-like wings and bare head." },
            { name: "Saddle-billed Stork", fact: "Has a striking black-and-yellow bill. It's one of the tallest storks in Africa." },
            { name: "Yellow-billed Hornbill", fact: "Famous from 'The Lion King' as Zazu. They seal themselves inside tree holes to nest." },
            { name: "Red-billed Oxpecker", fact: "Perches on large mammals like zebras and eats ticks and parasites from their skin." },
            { name: "Greater Flamingo", fact: "Gets its pink color from the algae and shrimp it eats. They sleep standing on one leg." },
            { name: "African Jacana", fact: "Has incredibly long toes that allow it to walk on floating lily pads — called 'Jesus birds.'" },
            { name: "Pied Kingfisher", fact: "Can hover in the air like a helicopter before diving straight down to catch fish." },
            { name: "Blue Waxbill", fact: "A tiny, bright blue bird often found in flocks. Its call sounds like a soft, high-pitched whistle." },
            { name: "Golden-tailed Woodpecker", fact: "Drills into bark to find insects. Its tongue is so long it wraps around its skull." },
            { name: "White-backed Vulture", fact: "Can spot a carcass from over a mile away. They play a vital role in cleaning the ecosystem." },
            { name: "Bateleur Eagle", fact: "Known for its short tail and rocking flight. The name means 'acrobat' in French." },
            { name: "Crested Barbet", fact: "Has a loud, trilling call that sounds like a cuckoo. Its bright red-and-yellow face is unmistakable." },
            { name: "Green Pigeon", fact: "One of the few pigeons that eats fruit almost exclusively. Its green plumage blends perfectly with leaves." },
            { name: "Red-eyed Dove", fact: "Its mournful call is a common sound in African woodlands. It builds flimsy nests of twigs." },
            { name: "Spotted Eagle-Owl", fact: "Has distinct ear tufts and piercing yellow eyes. It's one of the largest owls in southern Africa." },
            { name: "Hamerkop", fact: "Builds enormous nests — up to 1.5 meters across — that can support the weight of a human." },
            { name: "Blacksmith Lapwing", fact: "Named for its loud 'tink-tink' call that sounds like a blacksmith hammering metal." },
            { name: "African Hoopoe", fact: "Has a distinctive crown of feathers and a long, curved bill used to probe for insects." },
            { name: "Fiscal Shrike", fact: "Known as the 'butcher bird' because it impales prey on thorns to store for later." },
            { name: "Cape Glossy Starling", fact: "Its feathers are so iridescent they appear to change color from blue to purple in different light." },
            { name: "Namaqua Dove", fact: "Small and elegant with a long tail. The male has a striking black-and-white facial pattern." },
            { name: "Peregrine Falcon", fact: "The fastest animal on Earth — can dive at speeds over 380 km/h (240 mph)." },
            { name: "African Penguin", fact: "Lives off the coast of southern Africa. They have pink patches above their eyes that help with heat regulation." },
            { name: "Cape Cormorant", fact: "Excellent swimmers that dive to catch fish. Their feathers are not fully waterproof, so they spread their wings to dry." },
            { name: "Swift Tern", fact: "Migrates vast distances. Its sharp, pointed wings allow it to glide effortlessly over the ocean." },
            { name: "Grey Heron", fact: "Stands motionless in shallow water, waiting to spear fish with its dagger-like bill." },
            { name: "Little Egret", fact: "Has bright yellow feet that it uses to stir up prey in the water while hunting." },
            { name: "Sacred Ibis", fact: "Was revered in ancient Egypt and often mummified as a tribute to the god Thoth." },
            { name: "African Spoonbill", fact: "Feeds by sweeping its spoon-shaped bill side to side to catch small fish and insects." },
            { name: "White Stork", fact: "Famous for nesting on rooftops in Europe. It migrates to Africa every winter." },
            { name: "Blue Crane", fact: "South Africa's national bird. Its elegant, long feathers trail behind it in flight." },
            { name: "Wattled Crane", fact: "Has a distinctive red wattles hanging from its throat. It's one of the rarest cranes in Africa." },
            { name: "Kurrichane Thrush", fact: "Its song is one of the most beautiful and complex in the African bush." },
            { name: "Greater Honeyguide", fact: "Leads humans and animals to beehives. It eats the beeswax after the hive is broken open." },
            { name: "Brown Snake Eagle", fact: "Specializes in hunting snakes — it has thick, scaly legs to protect against bites." },
            { name: "Black-headed Oriole", fact: "Its bright yellow body and black head make it easy to spot. Its call is a clear, melodious whistle." },
            { name: "Red-billed Buffalo Weaver", fact: "Builds massive colonial nests in trees. The nests look like giant haystacks." },
            { name: "Magpie Shrike", fact: "Has a long, flowing tail and a bold black-and-white pattern. It's often seen perched on wires." },
            { name: "Rosy-faced Lovebird", fact: "A small parrot with a bright pink face. They are highly social and mate for life." },
            { name: "African Grey Hornbill", fact: "Often seen in pairs. They have a unique call that sounds like a cackling laugh." }
        ];

        // ============================================================
        // 2. BUILD SLIDES
        // ============================================================
        const wrapper = document.getElementById('slidesWrapper');
        const dotsContainer = document.getElementById('dotsContainer');

        // Use high-quality placeholder images from unsplash (free, reliable)
        // We'll use a consistent source: https://source.unsplash.com/featured/?bird,BIRDNAME
        // But to be safe, we'll use a generic bird search and append the species.
        // We'll use picsum? No, unsplash is better. We'll do: https://source.unsplash.com/800x450/?bird,name
        // Actually, to avoid broken images, we'll use a fixed pattern:
        // We'll use https://source.unsplash.com/featured/800x450/?bird (random bird)
        // But for variety, we'll include the bird name in the query.

        // We'll create a function that builds a slide for each bird.
        // For images, we'll use: https://source.unsplash.com/800x450/?bird,{encodedName}
        // This gives a high-quality bird photo.

        function buildSlides() {
            wrapper.innerHTML = '';
            birds.forEach((bird, index) => {
                const slide = document.createElement('div');
                slide.className = 'slide' + (index === 0 ? ' active' : '');
                slide.dataset.index = index;

                // Encode bird name for URL
                const encodedName = encodeURIComponent(bird.name);
                const imgSrc = `https://source.unsplash.com/800x450/?bird,${encodedName},wildlife`;

                slide.innerHTML = `
                    <img src="${imgSrc}" alt="${bird.name}" loading="lazy" onerror="this.src='https://source.unsplash.com/800x450/?bird,wild';" />
                    <div class="bird-name">${bird.name}</div>
                    <div class="bird-fact">${bird.fact}</div>
                `;
                wrapper.appendChild(slide);

                // Dot
                const dot = document.createElement('span');
                dot.className = 'dot' + (index === 0 ? ' active' : '');
                dot.dataset.index = index;
                dot.addEventListener('click', () => goToSlide(index));
                dotsContainer.appendChild(dot);
            });
        }

        // ============================================================
        // 3. SLIDESHOW LOGIC
        // ============================================================
        let currentIndex = 0;
        let slideInterval = null;
        const slides = () => document.querySelectorAll('.slide');
        const dots = () => document.querySelectorAll('.dot');

        function goToSlide(index) {
            const slidesList = slides();
            const dotsList = dots();
            if (!slidesList.length) return;
            if (index < 0) index = slidesList.length - 1;
            if (index >= slidesList.length) index = 0;

            slidesList.forEach(s => s.classList.remove('active'));
            dotsList.forEach(d => d.classList.remove('active'));

            slidesList[index].classList.add('active');
            dotsList[index].classList.add('active');
            currentIndex = index;
        }

        function nextSlide() {
            goToSlide(currentIndex + 1);
        }

        function startSlideshow() {
            if (slideInterval) clearInterval(slideInterval);
            slideInterval = setInterval(nextSlide, 6000);
        }

        // ============================================================
        // 4. AUDIO – YouTube embed with autoplay via iframe
        // ============================================================
        const audioBtn = document.getElementById('audioBtn');
        let isPlaying = false;
        let player = null;

        function loadAudio() {
            // Create a hidden iframe that loads the YouTube video with autoplay
            const container = document.getElementById('youtubeAudio');
            container.innerHTML = `
                <iframe id="ytPlayer" width="0" height="0" 
                    src="https://www.youtube.com/embed/fd0uuy4mDrE?autoplay=0&loop=1&playlist=fd0uuy4mDrE&controls=0&showinfo=0&modestbranding=1" 
                    frameborder="0" allow="autoplay; encrypted-media" 
                    style="display:none;">
                </iframe>
            `;
            // Note: We set autoplay=0 initially, but user must click to play.
        }

        function toggleAudio() {
            const iframe = document.getElementById('ytPlayer');
            if (!iframe) return;

            if (!isPlaying) {
                // Play: change src to autoplay=1
                const src = iframe.src;
                if (src.includes('autoplay=0')) {
                    iframe.src = src.replace('autoplay=0', 'autoplay=1');
                } else if (!src.includes('autoplay')) {
                    iframe.src = src + '&autoplay=1';
                } else {
                    // already autoplay=1
                }
                // Force reload to trigger play
                iframe.src = iframe.src.replace('&autoplay=0', '&autoplay=1');
                iframe.src = iframe.src + '&autoplay=1'; // fallback

                isPlaying = true;
                audioBtn.textContent = '🎵 Playing "So Into You"';
                audioBtn.classList.add('playing');
            } else {
                // Pause: we can't easily pause YouTube iframe without reloading, so we'll reload with autoplay=0
                const currentSrc = iframe.src;
                if (currentSrc.includes('autoplay=1')) {
                    iframe.src = currentSrc.replace('autoplay=1', 'autoplay=0');
                } else {
                    iframe.src = currentSrc + '&autoplay=0';
                }
                isPlaying = false;
                audioBtn.textContent = '🎵 Play "So Into You"';
                audioBtn.classList.remove('playing');
            }
        }

        // ============================================================
        // 5. INIT
        // ============================================================
        buildSlides();
        startSlideshow();
        loadAudio();

        // Click button to toggle audio
        audioBtn.addEventListener('click', toggleAudio);

        // Keyboard navigation (optional)
        document.addEventListener('keydown', (e) => {
            if (e.key === 'ArrowRight') nextSlide();
            if (e.key === 'ArrowLeft') goToSlide(currentIndex - 1);
        });

        // Pause slideshow on hover (optional)
        const container = document.querySelector('.slideshow-container');
        container.addEventListener('mouseenter', () => {
            if (slideInterval) clearInterval(slideInterval);
        });
        container.addEventListener('mouseleave', startSlideshow);

        console.log('🐦 50 Wild Wonders ready!');
    </script>
</body>
</html>
