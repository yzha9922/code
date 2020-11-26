# code
from microbit import *
import neopixel
import music

notes = [
    'c4#', 'g#', 'c5#', 'b4', 'g#', 'e5', 'c4#', 'b4', 'c5#', 'g4#', 'e5', 'b4', 'c5#', 'g4#'
]


if __name__ == '__main__':
    display.show(Image.YES)
    sleep(500)

    # Setup the Neopixel strip on pin1 with a length of 30 pixels
    np = neopixel.NeoPixel(pin1, 30)

    while True:
        a = int(pin2.read_analog())

        display.show(Image.MUSIC_QUAVER)

        if a <= 100:
            for pixel_id in range(0, len(np)):
                np[pixel_id] = (10,10,10)
                np.show()
        elif a <= 500:
            music.set_tempo(ticks=4, bpm=120)
            music.play(notes)
            value1 = 10
            while value1 <= 100:
                value1 += 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (value1,value1,value1)
                    np.show()
                sleep(8)
            while value1 >= 10:
                value1 -= 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (value1,value1,value1)
                    np.show()
                sleep(8)
        elif a <= 900:
            music.set_tempo(ticks=4, bpm=20)
            music.play(music.PRELUDE, wait=True)
            value2 = 10
            while value2 <= 250:
                value2 += 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (0,0,value2)
                    np.show()
                sleep(8)
            while value2 >= 10:
                value2 -= 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (0,0,value2)
                    np.show()
                sleep(8)
        else:
            music.set_tempo(ticks=4, bpm=40)
            music.play(music.ODE, wait=True)
            value3 = 10
            while value3 <= 250:
                value3 += 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (value3,0,0)
                    np.show()
                sleep(8)
            while value3 >= 10:
                value3 -= 5
                for pixel_id in range(0, len(np)):
                    np[pixel_id] = (value3,0,0)
                    np.show()
                sleep(8)


        sleep(500)
