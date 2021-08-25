<script lang="ts">
  import "twind/shim"
  import { tw } from "twind"
  import logo from "./assets/svelte.png"
  import Head from "./lib/Head.svelte"
  import Menu from "./lib/Menu.svelte"
  import Social from "./lib/Social.svelte"

  const url = "https://tcas.vercel.app"
  const title = "วาทะ TCAS สุดแจ่ม"

  const menuItems = []

  const description = "วาทะ TCAS สุดแจ่ม"
  const imageUrl = ""
  const gtagId = null

  const quotes: { q?: string; a: string }[] = [
    { q: "ทำไมไม่ตรวจ ATK คะ", a: "สร้างภาระมากครับ" },
    {
      q: "ถ้าติดโควิดก่อนสอบหรือติดจากตอนสอบจะมีมาตรการอะไรหลังจากนี้มั้ยคะ",
      a: "ติดก่อนสอบกักตัวเอง ติดจากการสอบควรไปรักษาและแจ้ง ทปอ เพื่อเตือนคนอื่นที่เสี่ยงไปด้วยครับ",
    },

    {
      q: "ถ้าหมอโทรให้กักตัวระหว่างช่วงสอบ มีวิธีแก้ยังไงบ้างคะ กังวลมากค่ะ",
      a: "ต้องกักตัวครับ สมัครสาขาที่ไม่ต้องใช้คะแนนสอบ",
    },

    {
      q: "ถ้าติดโควิดในสนามสอบ GAT PAT แล้วต้องไปสอบสนามสอบวิชาสามัญต่อ มีวิธีแก้ยังไงคะ",
      a: "เลือกสาขาที่ไม่ใช้คะแนนสามัญครับ",
    },

    {
      q: "หากต้องกักตัวหรือติดเชื้อก่อนวันสอบ จะทำยังไงครับ",
      a: "กักตัว รักษาตัว อาจเลือกสาขาที่ไม่ต้องใช้คะแนนสอบ",
    },

    {
      q: "สอบถามค่ะ ถ้ากรณีติดโควิดก่อนสอบ (หายไม่ทันวันสอบ) ต้องทำยังไงหรอคะ",
      a: "สอบปีหน้า หรือไม่ก็เลือกสาขาที่ไม่ต้องใช้คะแนนสอบครับ",
    },

    { q: "หากเกิดคลัสเตอร์ตั้งแต่สนามสอบแรก สนามต่อไปจะทำอย่างไรครับ", a: "รอเกิดก่อนนะครับ" },

    { a: "การเลื่อนสอบ ไม่ได้เป็นเหตุให้ Omicron หายไปจากประเทศไทยครับ" },

    {
      q: "พรบ.โรคติดต่อฯ กำหนดให้ผู้ป่วยไม่สามารถเดินทางออกจากที่กักตัวได้ จึงทำให้ผู้เข้าสอบไม่สามารถเดินทางมาสอบที่สนามสอบได้ และการสอบในสถานพยาบาล/Home Isolation/Hospitel ไม่สามารถปฏิบัติได้อย่างปลอดภัยและมีมาตรฐานเดียวกันกับการสอบทั่วไปอย่างเสมอภาคกัน อีกทั้งข้อสอบและกระดาษคำตอบอาจปนเปื้อนและแพร่เชื้อต่อไปได้ ขอให้ผู้เข้าสอบดูและรักษาตัวให้ปลอดภัยก่อนการสอบ",
      a: "ปัญหาเกิดจากใครคนนั้นควรแก้สิครับ",
    },
  ]

  let selectedQuote: { q?: string; a: string } = random()

  function random() {
    return quotes[Math.floor(Math.random() * quotes.length)]
  }
</script>

<Menu items={menuItems} />
<Head {title} {description} {url} {imageUrl} {gtagId} />

<main class="bg-black w-full h-screen p-4 flex flex-col justify-center items-center">
  <h1 class="text-6xl text-pink-400 flex flex-col text-center">
    <span>วาทะ</span><span>TCAS</span><span>สุดแจ่ม</span>
  </h1>

  <div>
    {#if selectedQuote.q}
      <p class="mt-6 text-xl text-center text-gray-600 bg-gray-300 p-4 rounded">
        {selectedQuote.q}
      </p>
    {/if}

    <p class="mt-6 text-3xl text-center bg-yellow-300 p-8 rounded">"{selectedQuote.a}"</p>
  </div>

  <div class="mt-4">
    <button
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded text-xl"
      on:click={() => (selectedQuote = random())}>สุ่มใหม่</button
    >
  </div>

  <Social {url} {title} />
</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell,
      "Open Sans", "Helvetica Neue", sans-serif;
  }
</style>
