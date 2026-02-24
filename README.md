  #oops-banner
  import java.util.HashMap;
import java.util.Map;

public class BannerApp {

    public static void main(String[] args) {
        String word = "OOPS";
        printBanner(word);
    }

    public static void printBanner(String word) {
        int patternHeight = 5;

        StringBuilder[] bannerLines = new StringBuilder[patternHeight];
        for (int i = 0; i < patternHeight; i++) {
            bannerLines[i] = new StringBuilder();
        }

        for (char ch : word.toCharArray()) {
            CharacterPatternMap pattern = CharacterPatternMap.getPattern(ch);

            if (pattern == null) {
                throw new IllegalArgumentException("No pattern found for character: " + ch);
            }

            String[] lines = pattern.getPattern();

            for (int i = 0; i < patternHeight; i++) {
                bannerLines[i].append(lines[i]).append("  ");
            }
        }

        for (StringBuilder line : bannerLines) {
            System.out.println(line.toString());
        }
    }

    // ✅ Static Inner Class (UC7 requirement)
    static class CharacterPatternMap {
        private char character;
        private String[] pattern;

        private static final Map<Character, CharacterPatternMap> patterns = new HashMap<>();

        // Constructor
        public CharacterPatternMap(char character, String[] pattern) {
            this.character = character;
            this.pattern = pattern;
        }

        // Getter
        public char getCharacter() {
            return character;
        }

        public String[] getPattern() {
            return pattern;
        }

        // Register all characters here
        static {
            patterns.put('O', new CharacterPatternMap('O', new String[]{
                    " *** ",
                    "*   *",
                    "*   *",
                    "*   *",
                    " *** "
            }));

            patterns.put('P', new CharacterPatternMap('P', new String[]{
                    "**** ",
                    "*   *",
                    "**** ",
                    "*    ",
                    "*    "
            }));

            patterns.put('S', new CharacterPatternMap('S', new String[]{
                    " ****",
                    "*    ",
                    " *** ",
                    "    *",
                    "**** "
            }));
        }

        public static CharacterPatternMap getPattern(char ch) {
            return patterns.get(Character.toUpperCase(ch));
        }
    }
}
