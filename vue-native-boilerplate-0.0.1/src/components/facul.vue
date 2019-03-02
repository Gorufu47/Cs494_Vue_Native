<template>
  <view>
    <button
        :on-press="onPressLearnMore1"
        title="วิทยาลัยบริหารศาสตร์"
        color="#ff0080"
    />

    <button
        :on-press="onPressLearnMore2"
        title="วิทยาลัยพลังงานทดแทน"
        color="#00b300"
    />

    <button
        :on-press="onPressLearnMore3"
        title="สารสนเทศและการสื่อสาร"
        color="#4d79ff"
    />
  </view>
</template>

<script>
export default {
    methods: {
        onPressLearnMore1: function() {
            alert('รัฐประศาสนศาสตร์ Public Administration'),
            alert('รัฐศาสตร์ Public Political Science'),
            alert('การบริหารท้องถิ่น Local Administration')
        },
        onPressLearnMore2: function() {
            alert('วิศวกรรมการอนุรักษ์พลังงาน Energy Conservation Engineering'),
            alert('พลังงานทดแทน Renewable Energy'),
            alert('พลังงานทดแทน Bachelor of Science Program in Renewable Energy')
        },
        onPressLearnMore3: function() {
            alert('การสื่อสารดิจิทัล Bachelor of Arts Program in Digital Communication'),
            alert('การสื่อสารดิจิทัล Bachelor of Arts Program in Digital Communication 2 Year')
        }
    }
};
</script>

<style>
</style>
