

### Hi i'm lamiiz 👋

## [![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Lemon+milk&color=F7000&lines=Hi...++im+lamiiz;Welcome+to+my+profile;full+stack+developer)](https://git.io/typing-svg)
#### TOTAL profile VIEWSERS📍
## ![Visitor Count](https://profile-counter.glitch.me/typegrapher/count.svg)


# Hi ,<a href="Hey"><img src="https://raw.githubusercontent.com/TOXIC-DEVIL/TOXIC-DEVIL/TOXIC-DEVIL-OFFICIAL/media/Hi.gif" width="48px"></a> I'm lamiiz&nbsp;




- 🔭 I’m currently working on [lamiiz] (https://github.com/lamiiz)

- 💬 Ask me about *ME*

- 📫 How to reach me *https://wa.me/919946803234*

- ⚡ Fun fact *I THINK IAM VERY POSITIVE*


## Connect with Me


[<img align="left" alt="Instagram" height="40px" width="40px" src="images/instagram.png" />](https://www.instagram.com/_lamii.__x/)
[<img align="left" alt="LinkedIn" height="40px" width="40px" src="images/linkedin.png" />](https://www.linkedin.com/in/muhammed-lamees-mv-4970ba260/)
[<img align="left" alt="Facebook" height="40px" width="40px" src="images/facebook.png" />](https://www.facebook.com/profile.php?id=100017169841207)
[<img align="left" alt="WhatsApp" height="40px" width="40px" src="images/whatsapp.png" />](https://api.whatsapp.com/send/?phone=919946803234&text&type=phone_number&app_absent=0)

<br clear="left">

## portfolio


[![Image Description](https://i.ibb.co/qWjRk4x/Screenshot-from-2023-08-07-12-25-01.png)](https://muhammedlamees.great-site.net/)



uint64_t
riscv_rtclock_read_cnt(void)
{
#if __riscv_xlen == 32
  // Atomic read. The loop is taken once in most cases. Only when the
  // value carries to the high word, two loops are performed.
  while (true)
    {
      uint32_t hi = rtclock.cnth;
      uint32_t lo = rtclock.cntl;
      if (hi == rtclock.cnth)
        {
          return ((uint64_t) hi << 32) | lo;
        }
    }
#else
  return rtclock.cnt;
#endif
}

uint64_t
riscv_rtclock_read_cmp(void)
{
#if __riscv_xlen == 32
  return ((uint64_t) hcb.rtclockcmph << 32) | hcb.rtclockcmpl;
#else
  return dcb.rtclock.cmp;
#endif
}

void
riscv_rtclock_write_cmp(uint64_t value)
{
#if __riscv_xlen == 32
  // Write low as max; no smaller than old value.
  hcb.rtclockcmpl = (uint32_t) UINT_MAX;
  // Write high; no smaller than old value.
  hcb.rtclockcmph = ((uint32_t) (value >> 32));
  // Write low as new value.
  hcb.rtclockcmpl = ((uint32_t) value);
#else
  hcb.rtclockcmp = value;
#endif
}
