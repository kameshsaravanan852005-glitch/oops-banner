# oops-banner 
 public class UCBannerOPS {

    public static void main(String[] args) {

        String[] banner = buildOPS();

        for (String line : banner) {
            System.out.println(line);
        }
    }

    // Builds OPS banner using helper methods
    static String[] buildOPS() {
        String[] o = buildO();
        String[] p = buildP();
        String[] s = buildS();

        String[] banner = new String[o.length];

        for (int i = 0; i < o.length; i++) {
            banner[i] = o[i] + "  " + p[i] + "  " + s[i];
        }

        return banner;
    }

    static String[] buildO() {
        return new String[] {
            " ### ",
            "#   #",
            "#   #",
            "#   #",
            " ### "
        };
    }

    static String[] buildP() {
        return new String[] {
            "#### ",
            "#   #",
            "#### ",
            "#    ",
            "#    "
        };
    }

    static String[] buildS() {
        return new String[] {
            " ####",
            "#    ",
            " ### ",
            "    #",
            "#### "
        };
    }
}
