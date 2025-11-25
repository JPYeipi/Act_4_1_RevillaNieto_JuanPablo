<template>
  <div class="slider-container">
    <CardBackground>
      <div class="slider-content">
        <button class="nav-button left-button" @click="prevSlide" :disabled="currentSlide === 0">
          <img :src="leftArrow" alt="Anterior" class="arrow-icon">
        </button>
        
        <InnerCard>
          <div class="inner-content">
            <div class="top-section">
              <ImageSquare 
                :image-src="currentCard.image"
                :alt-text="currentCard.title"
                :placeholder-text="'Imagen'"
                class="image-component"
              />
              
              <div class="text-section">
                <TextRectangle 
                  :title="currentCard.title"
                  class="title-rectangle"
                />
                <TextRectangle 
                  :content="currentCard.subtitle"
                  class="subtitle-rectangle"
                />
              </div>
            </div>
            
            <!-- Sección inferior -->
            <div class="bottom-section">
              <ContentRectangle 
                :title="currentCard.contentTitle"
                :content="currentCard.content"
                class="content-component"
              />
            </div>
          </div>
        </InnerCard>
        
        <button class="nav-button right-button" @click="nextSlide" :disabled="currentSlide === cards.length - 1">
          <img :src="rightArrow" alt="Siguiente" class="arrow-icon">
        </button>
      </div>
    </CardBackground>
    
  </div>
</template>

<script>
import CardBackground from './Card1.vue'
import InnerCard from './Card2.vue'
import ImageSquare from './Image.vue'
import TextRectangle from './Title.vue'
import ContentRectangle from './Desc.vue'

export default {
  name: 'SliderComponent',
  components: {
    CardBackground,
    InnerCard,
    ImageSquare,
    TextRectangle,
    ContentRectangle
  },
  props: {
    cards: {
      type: Array,
      required: true
    },
    leftArrow: {
      type: String,
      required: true
    },
    rightArrow: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      currentSlide: 0
    }
  },
  computed: {
    currentCard() {
      return this.cards[this.currentSlide] || {}
    }
  },
  methods: {
    nextSlide() {
      if (this.currentSlide < this.cards.length - 1) {
        this.currentSlide++
      }
    },
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide--
      }
    },
    goToSlide(index) {
      this.currentSlide = index
    }
  }
}
</script>

<style scoped>
.slider-container {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

.slider-content {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
  z-index: 10;
  transition: all 0.3s ease;
}

.left-button {
  left: 10px;
}

.right-button {
  right: 10px;
}

.arrow-icon {
  width: 32px;
  height: 32px;
  transition: all 0.3s ease;
}

.nav-button:hover .arrow-icon {
  filter: brightness(0) saturate(100%) invert(60%) sepia(0%) saturate(0%) hue-rotate(0deg) brightness(50%);
}

.nav-button:disabled {
  opacity: 0.3;
  cursor: not-allowed;
}

.nav-button:disabled:hover .arrow-icon {
  filter: none;
}

.inner-content {
  width: 100%;
  height: 100%;
  padding: 30px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.top-section {
  display: flex;
  gap: 30px;
  align-items: flex-start;
}

.text-section {
  display: flex;
  flex-direction: column;
  gap: 15px;
  flex: 1;
}

.bottom-section {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.slider-indicators {
  display: flex;
  gap: 10px;
  margin-top: 20px;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  border: none;
  background-color: var(--color-gray);
  cursor: pointer;
  transition: all 0.3s ease;
}

.indicator.active {
  background-color: var(--color-primary);
}

.indicator:hover {
  background-color: var(--color-primary-hover);
}

/* Responsive */
@media (max-width: 768px) {
  .inner-content {
    padding: 20px;
    gap: 20px;
  }
  
  .top-section {
    flex-direction: column;
    gap: 20px;
    align-items: center;
  }
  
  .text-section {
    width: 100%;
  }
  
  .nav-button {
    padding: 5px;
  }
  
  .arrow-icon {
    width: 24px;
    height: 24px;
  }
}

@media (max-width: 480px) {
  .inner-content {
    padding: 15px;
    gap: 15px;
  }
  
  .top-section {
    gap: 15px;
  }
  
  .arrow-icon {
    width: 20px;
    height: 20px;
  }
  
  .slider-indicators {
    gap: 8px;
  }
  
  .indicator {
    width: 10px;
    height: 10px;
  }
}
</style>