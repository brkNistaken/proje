<template>
  <div class="filter-container">
    <!-- Beden Durumu Filter -->
    <div class="filter-item">
      <div
        class="flex justify-between items-center cursor-pointer"
        @click="toggleSection('bedenDurumu')"
      >
        <span class="font-medium text-sm">Beden Durumu</span>
        <span>
          <svg
            :class="{ rotated: sectionsVisibility.bedenDurumu }"
            stroke="currentColor"
            fill="currentColor"
            stroke-width="0"
            viewBox="0 0 24 24"
            height="20"
            width="20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="m6.293 13.293 1.414 1.414L12 10.414l4.293 4.293 1.414-1.414L12 7.586z"
            ></path>
          </svg>
        </span>
      </div>
      <div class="filter-options" v-if="sectionsVisibility.bedenDurumu">
        <div class="filter-option">
          <input
            type="checkbox"
            id="stokta"
            v-model="filters.stokta"
          />
          <label for="stokta" class="text-xs">
            Stokta <span class="text-xs text-gray-500">(5)</span>
          </label>
        </div>
        <div class="filter-option">
          <input
            type="checkbox"
            id="stokta-yok"
            v-model="filters.stoktaYok"
          />
          <label for="stokta-yok" class="text-xs">
            Stokta yok <span class="text-xs text-gray-500">(5)</span>
          </label>
        </div>
      </div>
    </div>

    <!-- Fiyat Slider -->
    <div class="slider-container">
      <div class="slider-header" @click="toggleSection('fiyat')">
        <span class="font-medium text-sm">Fiyat</span>
        <span>
          <svg
            :class="{ rotated: sectionsVisibility.fiyat }"
            stroke="currentColor"
            fill="currentColor"
            stroke-width="0"
            viewBox="0 0 24 24"
            height="20"
            width="20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="m6.293 13.293 1.414 1.414L12 10.414l4.293 4.293 1.414-1.414L12 7.586z"
            ></path>
          </svg>
        </span>
      </div>

      <div class="slider-background-wrapper" v-if="sectionsVisibility.fiyat">
        <div class="slider-background" style="position: relative; width: 100%; height: 7px;">
          <div
            class="slider-track"
            style="position: absolute; width: 100%; height: 7px; border-radius: 7px; background-color: rgb(214, 214, 214);"
          ></div>

          <div
            class="slider-handle"
            :style="{ left: minPercentage + '%' }"
            @mousedown="startDrag('min')"
            @click="updateMinValue"
            role="slider"
            aria-valuemin="0"
            aria-valuemax="1000"
            :aria-valuenow="minValue"
          >
            <div class="tooltip">
              <span class="tooltiptext">{{ minValue }}₺</span>
            </div>
          </div>

          <div
            class="slider-handle"
            :style="{ left: maxPercentage + '%' }"
            @mousedown="startDrag('max')"
            @click="updateMaxValue"
            role="slider"
            aria-valuemin="0"
            aria-valuemax="1000"
            :aria-valuenow="maxValue"
          >
            <div class="tooltip">
              <span class="tooltiptext">{{ maxValue }}₺</span>
            </div>
          </div>

          <div
            class="slider-tracks"
            :style="{
              left: minPercentage + '%',
              width: maxPercentage - minPercentage + '%',
            }"
            style="position: absolute; height: 7px; z-index: 1; background-color: black; border-radius: 7px; cursor: pointer;"
          ></div>
        </div>
      </div>

      <div class="values-display" v-if="sectionsVisibility.fiyat">
        <span>{{ minValue }}₺</span>
        <span>{{ maxValue }}₺</span>
      </div>
    </div>

    <!-- Beden Filter -->
    <div class="filter-item">
      <div
        class="flex justify-between items-center cursor-pointer"
        @click="toggleSection('beden')"
      >
        <span class="font-medium text-sm">Beden</span>
        <span>
          <svg
            :class="{ rotated: sectionsVisibility.beden }"
            stroke="currentColor"
            fill="currentColor"
            stroke-width="0"
            viewBox="0 0 24 24"
            height="20"
            width="20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="m6.293 13.293 1.414 1.414L12 10.414l4.293 4.293 1.414-1.414L12 7.586z"
            ></path>
          </svg>
        </span>
      </div>

      <div class="filters-scrollable" v-if="sectionsVisibility.beden">
        <div class="mb-3 w-11/12 relative">
          <input
            type="text"
            class="filter-search-input"
            placeholder="Filtrele"
            value=""
          />
          <span class="filter-search-icon">
            <svg
              stroke="currentColor"
              fill="currentColor"
              stroke-width="0"
              viewBox="0 0 24 24"
              height="15"
              width="15"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M18.031 16.6168L22.3137 20.8995L20.8995 22.3137L16.6168 18.031C15.0769 19.263 13.124 20 11 20C6.032 20 2 15.968 2 11C2 6.032 6.032 2 11 2C15.968 2 20 6.032 20 11C20 13.124 19.263 15.0769 18.031 16.6168ZM16.0247 15.8748C17.2475 14.6146 18 12.8956 18 11C18 7.1325 14.8675 4 11 4C7.1325 4 4 7.1325 4 11C4 14.8675 7.1325 18 11 18C12.8956 18 14.6146 17.2475 15.8748 16.0247L16.0247 15.8748Z"
              ></path>
            </svg>
          </span>
        </div>

        <div class="filter-option">
          <input
            type="checkbox"
            id="bedenL"
            v-model="filters.beden.L"
          />
          <label for="bedenL" class="text-xs">
            L <span class="text-xs text-gray-500">(2)</span>
          </label>
        </div>
        <div class="filter-option">
          <input
            type="checkbox"
            id="bedenM"
            v-model="filters.beden.M"
          />
          <label for="bedenM" class="text-xs">
            M <span class="text-xs text-gray-500">(4)</span>
          </label>
        </div>
        <div class="filter-option">
          <input
            type="checkbox"
            id="bedenS"
            v-model="filters.beden.S"
          />
          <label for="bedenS" class="text-xs">
            S <span class="text-xs text-gray-500">(3)</span>
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sectionsVisibility: {
        bedenDurumu: true,
        fiyat: true,
        beden: true,
      },
      filters: {
        stokta: false,
        stoktaYok: false,
        beden: {
          L: false,
          M: false,
          S: false,
        },
      },
      minValue: 0,
      maxValue: 1000,
      minPercentage: 0,
      maxPercentage: 100,
      isDragging: false,
      activeHandle: null,
    };
  },
  methods: {
    toggleSection(section) {
      this.$set(this.sectionsVisibility, section, !this.sectionsVisibility[section]);
    },
    startDrag(handle) {
      this.isDragging = true;
      this.activeHandle = handle;
      document.addEventListener("mousemove", this.onMouseMove);
      document.addEventListener("mouseup", this.stopDrag);
    },
    updateMinValue(event) {
      const sliderWidth = this.$el.querySelector(".slider-background").offsetWidth;
      let newPercentage = ((event.clientX - this.$el.querySelector(".slider-background").getBoundingClientRect().left) / sliderWidth) * 100;
      newPercentage = Math.max(0, Math.min(newPercentage, this.maxPercentage));
      this.minPercentage = newPercentage;
      this.minValue = Math.round((newPercentage / 100) * 1000);
    },
    updateMaxValue(event) {
      const sliderWidth = this.$el.querySelector(".slider-background").offsetWidth;
      let newPercentage = ((event.clientX - this.$el.querySelector(".slider-background").getBoundingClientRect().left) / sliderWidth) * 100;
      newPercentage = Math.max(this.minPercentage, Math.min(newPercentage, 100));
      this.maxPercentage = newPercentage;
      this.maxValue = Math.round((newPercentage / 100) * 1000);
    },
    onMouseMove(event) {
      if (this.isDragging && this.activeHandle) {
        if (this.activeHandle === "min") {
          this.updateMinValue(event);
        } else if (this.activeHandle === "max") {
          this.updateMaxValue(event);
        }
      }
    },
    stopDrag() {
      this.isDragging = false;
      this.activeHandle = null;
      document.removeEventListener("mousemove", this.onMouseMove);
      document.removeEventListener("mouseup", this.stopDrag);
    },
  },
};
</script>

<style scoped>
.filter-container {
  display: flex;
  flex-direction: column;
  margin: 20px;
}
.filter-item {
  margin-bottom: 20px;
}
.rotated {
  transform: rotate(180deg);
}
.filter-option {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 5px 0;
}
.slider-container {
  margin-top: 20px;
}
.slider-background-wrapper {
  width: 100%;
  height: 7px;
  position: relative;
}
.slider-track {
  width: 100%;
  height: 7px;
  background-color: rgb(214, 214, 214);
  border-radius: 7px;
}
.slider-handle {
  position: absolute;
  height: 15px;
  width: 15px;
  border-radius: 50%;
  background-color: black;
  top: 50%;
  transform: translateY(-50%);
}
.tooltip {
  position: absolute;
  top: -25px;
  left: -15px;
  color: white;
  font-size: 12px;
}
.filter-search-input {
  padding: 8px;
  border-radius: 8px;
  border: 1px solid #ccc;
  width: 100%;
  box-sizing: border-box;
}
.filter-search-icon {
  position: absolute;
  top: 50%;
  right: 10px;
  transform: translateY(-50%);
}
.values-display {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
}
</style>
