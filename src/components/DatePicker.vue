<template>
  <div class="wrapper">
    <div class="date-time">
      <div class="section section-date" :class="{'is-active': display.date}">
        <div class="active-item" @click="display.date = !display.date">
          <span v-text="dateStamp"></span>
          <label v-if="!display.date">click to change</label>
        </div>
        <div class="item" v-if="display.date" v-for="(format, index) in dateFormats" @click="activeIndex.date = index; display.date = false">
          <span v-text="getDateFromFormat(format)"></span>
        </div>
      </div>
      <div class="section section-time" :class="{'is-active': display.time}">
        <div class="active-item" @click="display.time = !display.time">
          <span v-text="timeStamp"></span>
          <label v-if="!display.time">click to change</label>
        </div>
        <div class="item" v-if="display.time" v-for="(format, index) in timeFormats" @click="activeIndex.time = index; display.time = false">
          <span v-text="getTimeFromFormat(format)"></span>
        </div>
      </div>
    </div>
    <div class="display-formats">
      <div class="format">
        <label>PHP</label>
        <span>date('<strong v-text="formatStringPhp"></strong>');</span>
      </div>
      <div class="format">
        <label>Moment.js</label>
        <span>moment.format('<strong v-text="formatStringMoment"></strong>');</span>
      </div>
    </div>
  </div>
</template>

<script>
  import moment from 'moment'

  export default {
    data () {
      return {
        now: new Date(),
        activeIndex: {
          date: 0,
          time: 0
        },
        dateFormats: [
          {
            moment: 'MM/DD/YYYY',
            php: 'm/d/Y'
          },
          {
            moment: 'MM/DD/YY',
            php: 'm/d/y'
          },
          {
            moment: 'MMM D, YYYY',
            php: 'M n, Y'
          },
          {
            moment: 'MMM DD, YYYY',
            php: 'M d, Y'
          },
          {
            moment: 'MMMM D, YYYY',
            php: 'F n, Y'
          },
          {
            moment: 'MMMM DD, YYYY',
            php: 'F d, Y'
          }
        ],
        timeFormats: [
          {
            moment: 'h:mm:ss a',
            php: 'g:i:s a'
          },
          {
            moment: 'h:mm a',
            php: 'g:i a'
          },
          {
            moment: 'hh:mm:ss a',
            php: 'h:i:s a'
          },
          {
            moment: 'HH:mm:ss a',
            php: 'H:i:s a'
          },
          {
            moment: 'H:mm:ss a',
            php: 'G:i:s a'
          },
          {
            moment: 'HH:mm:ss A',
            php: 'H:i:s A'
          }
        ],
        display: {
          date: false,
          time: false
        }
      }
    },
    created () {
      setInterval(() => {
        this.now = new Date()
      }, 1000)
    },
    methods: {
      getDateFromFormat (format) {
        return moment(this.now).format(format.moment)
      },
      getTimeFromFormat (format) {
        return moment(this.now).format(format.moment)
      }
    },
    computed: {
      dateStamp () {
        return moment(this.now).format(this.dateFormats[this.activeIndex.date].moment)
      },
      timeStamp () {
        return moment(this.now).format(this.timeFormats[this.activeIndex.time].moment)
      },
      formatStringPhp () {
        return this.dateFormats[this.activeIndex.date].php + ' ' + this.timeFormats[this.activeIndex.time].php
      },
      formatStringMoment () {
        return this.dateFormats[this.activeIndex.date].moment + ' ' + this.timeFormats[this.activeIndex.time].moment
      }
    }
  }
</script>

<style>
  .wrapper {
    margin: 0 auto;
    max-width: 960px;
  }
  .date-time {
    margin: 0 auto;
    position: relative;
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    height: 112px;
    overflow: visible;
  }
  .section {
    background: #fff;
    vertical-align: top;
    margin: 0 1rem;
    border-radius: 4px;
    box-shadow: 0 0 0 rgba(30, 39, 46, 0);
    transition: all 0.25s ease-in;
    padding: 0.75rem 1.5rem 2rem;
    color: #1E272E;
  }
  .section:hover {
    cursor: pointer;
    box-shadow: 0 2px 17px rgba(30, 39, 46, 0.15);
  }
  .section.is-active {
    box-shadow: 0 2px 17px rgba(30, 39, 46, 0.15);
  }
  .active-item {
    position: relative;
  }
  .active-item span {
    font-weight: 700;
    font-size: 56px;
  }
  .active-item label {
    display: block;
    position: absolute;
    pointer-events: none;
    left: 0;
    bottom: -1rem;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: #808E9B;
  }
  .item {
    text-align: left;
    padding: 0.5rem 0;
    color: #808E9B;
    transition: all 0.25s ease-in;
  }
  .item:hover {
    cursor: pointer;
    color: #F53B57;
  }
  .item span {
    font-weight: 700;
    font-size: 27px;
  }
  .display-formats {
    margin: 4rem 0 0 2.5rem;
  }
  .format {
    text-align: left;
    margin: 0 0 2rem;
  }
  .format label {
    display: block;
    font-size: 14px;
    font-weight: 700;
    text-transform: uppercase;
    color: #F53B57;
    letter-spacing: 1px;
    margin: 0 0 0.25rem;
  }
  .format span {
    display: inline-block;
    padding: 0.75rem 1rem;
    border: 1px solid #D2DAE2;
    border-radius: 4px;
    font-family: "IBM Plex Mono", monospace;
    font-weight: 400;
    color: #808E9B;
  }
  .format span strong {
    font-weight: 700;
    color: #485460;
  }
</style>