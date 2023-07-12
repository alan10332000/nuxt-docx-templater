<template>
  <div>
    <input type="file" @change="handleFileChange" />
  </div>
</template>

<script>
import { saveAs } from 'file-saver'
import { generateDocxFile } from '../lib/generate-docx'

const fileData = {
  intro: '國際勞動節，又稱五一國際勞動節、勞動節、國際示威遊行日，是紀念工人和勞工運動的鬥爭和成果的日子。國際勞動節是一項由國際勞工運動所推動的節日，全世界勞工和工人階級在一般會在五朔節（5月1日）舉行的慶祝節日，而美國和加拿大在9月第一個星期一舉行。是世界上80多個國家的勞動節。',
  activities: [
    {
      name: '阿爾及利亞',
      activity: '在阿爾及利亞，5月1日是公共假日，以慶祝勞動節。'
    },
    {
      name: '安哥拉',
      activity: '5月1日在安哥拉被承認為公共假日，稱為勞動節。'
    },
    {
      name: '埃及',
      activity: '在埃及，5月1日被稱為勞動節，是一個帶薪的公共假期。在傳統上，埃及總統會主持正式的五一節慶祝活動。'
    },
    {
      name: '迦納',
      activity: '5月1日是迦納的一個節日，屬於慶祝全國所有工人。工會和勞工協會以遊行的形式來慶祝勞動節。迦納也會舉行閱兵式，通常由工會大會秘書長和各地區的區域秘書致辭。來自不同工作地點的工人通過條幅和衣著表明他們的公司。'
    }
  ]
}

export default {
  name: 'IndexPage',
  methods: {
    async handleFileChange (e) {
      const file = e.target.files[0]
      const out = await generateDocxFile(file, fileData)
      saveAs(out, `${new Date().getTime()}.docx`)
    }
  },
}
</script>
